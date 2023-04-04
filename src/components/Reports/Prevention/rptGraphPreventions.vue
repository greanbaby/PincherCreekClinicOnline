<template>
    <div class="card">
        <Chart type="bar" :data="chartData" :options="chartOptions" class="charto"  />
    </div>
</template>

<script setup>
import { ref, onMounted, computed } from "vue";
import Chart from 'primevue/chart';
const myProps = defineProps([ 'chosenReportDetails', 'chosenReportTotals' ]);
onMounted(() => {
    chartData.value = setChartData();
    chartOptions.value = setChartOptions();
});

const chosenRptData = computed(() => {
    return [ ( (myProps.chosenReportDetails.BP_Numerator / myProps.chosenReportDetails.BP_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportDetails.CRC_Numerator / myProps.chosenReportDetails.CRC_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportDetails.Exercise_Numerator / myProps.chosenReportDetails.Exercise_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportDetails.Height_Numerator / myProps.chosenReportDetails.Height_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportDetails.Mammo_Numerator / myProps.chosenReportDetails.Mammo_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportDetails.Pap_Numerator / myProps.chosenReportDetails.Pap_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportDetails.Smoking_Numerator / myProps.chosenReportDetails.Smoking_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportDetails.Weight_Numerator / myProps.chosenReportDetails.Weight_Denominator) * 100 ).toFixed( 1 )
        ];
});

const chosenPhysician = computed(() => {
    return myProps.chosenReportDetails.physician;
});

const chosenRptTotals = computed(() => {
    return [ ( (myProps.chosenReportTotals.BP_Numerator / myProps.chosenReportTotals.BP_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportTotals.CRC_Numerator / myProps.chosenReportTotals.CRC_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportTotals.Exercise_Numerator / myProps.chosenReportTotals.Exercise_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportTotals.Height_Numerator / myProps.chosenReportTotals.Height_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportTotals.Mammo_Numerator / myProps.chosenReportTotals.Mammo_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportTotals.Pap_Numerator / myProps.chosenReportTotals.Pap_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportTotals.Smoking_Numerator / myProps.chosenReportTotals.Smoking_Denominator) * 100 ).toFixed( 1 ),
            ( (myProps.chosenReportTotals.Weight_Numerator / myProps.chosenReportTotals.Weight_Denominator) * 100 ).toFixed( 1 )
        ];
});

const chartData = ref();
const chartOptions = ref();

const setChartData = () => {
    const documentStyle = getComputedStyle(document.documentElement);

    return {
        labels: ['Blood Pressure',
            'Colorectal Cancer Screen',
            'Exercise Assessment',
            'Height',
            'Mammography',
            'Pap Test',
            'Tobacco Use Assessment',
            'Weight'
        ],
        datasets: [
            {
            label: chosenPhysician,
            backgroundColor: 'hsla(160, 100%, 37%, 0.5)',
            
            data: chosenRptData
        },
        {
            label: 'Average',
            backgroundColor: 'rgb(226, 226, 226)',
            
            data: chosenRptTotals
        }
        ]
    };
};
const setChartOptions = () => {
    const documentStyle = getComputedStyle(document.documentElement);
    const textColor = documentStyle.getPropertyValue('--text-color');
    const textColorSecondary = documentStyle.getPropertyValue('--text-color-secondary');
    const surfaceBorder = 'rgb(226, 226, 226)';

    return {
        maintainAspectRatio: false,
        aspectRatio: 0.8,
        plugins: {
            legend: {
                labels: {
                    fontColor: textColor
                }
            }
        },
        scales: {
            x: {
                ticks: {
                    color: textColorSecondary,
                    font: {
                        weight: 500
                    }
                },
                grid: {
                    display: false,
                    drawBorder: false
                }
            },
            y: {
                ticks: {
                    color: textColorSecondary
                },
                grid: {
                    color: surfaceBorder,
                    drawBorder: false
                }
            }
        }
    };
}
</script>
<style scoped>
.card {
    border-left: 1px solid hsla(160, 100%, 37%, 0.5);
    border-right: 1px solid hsla(160, 100%, 37%, 0.5);
    border-bottom: 1px solid hsla(160, 100%, 37%, 0.5);
}
.charto {
    margin: 0;
}
</style>