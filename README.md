Affichage de tpt
=======================

STM 32F4 + afficheur 7 segments 4 digits + Capteur Lm35 

-------
/* Includes */
#include "stm32f4xx.h"
#include "stm32f4_discovery.h"
#include "stm32f4xx_gpio.h"
#include "stm32f4xx_adc.h"
#include "stm32f4xx_rcc.h"
/* Private macro */
/* Private variables */
/* Private function prototypes */
/* Private functions */

/**
 **===========================================================================
 **
 ** ADC+LM35_NADA
 **
 **===========================================================================
 */

GPIO_InitTypeDef GPIO_InitStructure;
void init() {

	RCC_AHB1PeriphClockCmd(RCC_AHB1Periph_GPIOD, ENABLE);
	RCC_AHB1PeriphClockCmd(RCC_AHB1Periph_GPIOB, ENABLE);

	GPIO_InitStructure.GPIO_Pin = GPIO_Pin_11 | GPIO_Pin_12 | GPIO_Pin_13 | GPIO_Pin_14  |GPIO_Pin_5 | GPIO_Pin_7 | GPIO_Pin_8 | GPIO_Pin_4 | GPIO_Pin_6 ;
	GPIO_InitStructure.GPIO_Mode = GPIO_Mode_OUT;
	GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
	GPIO_Init(GPIOB, &GPIO_InitStructure);

	GPIO_InitStructure.GPIO_Pin = GPIO_Pin_12 | GPIO_Pin_2 | GPIO_Pin_3
			| GPIO_Pin_5 | GPIO_Pin_6 | GPIO_Pin_0 ;
	GPIO_InitStructure.GPIO_Mode = GPIO_Mode_OUT;
	GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
	GPIO_Init(GPIOD, &GPIO_InitStructure);
}
void delay(int x) {
	int j;
	for (j = 0; j < (1200000) * x; j++)
		; //delay
}

void ecrire(int n) {
	switch (n) {
	case 0:
	   GPIO_ResetBits(GPIOD, GPIO_Pin_0);
	   GPIO_ResetBits(GPIOD, GPIO_Pin_2);
	   GPIO_ResetBits(GPIOD, GPIO_Pin_3);
	   GPIO_ResetBits(GPIOB, GPIO_Pin_8);
	   GPIO_ResetBits(GPIOB, GPIO_Pin_5);
	   GPIO_ResetBits(GPIOB, GPIO_Pin_6);
	   GPIO_SetBits(GPIOB, GPIO_Pin_7);
	 //  GPIO_SetBits(GPIOB, GPIO_Pin_12);
		break;
	case 1:

		       GPIO_SetBits(GPIOD, GPIO_Pin_0);
			   GPIO_SetBits(GPIOD, GPIO_Pin_2);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_3);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_8);
			   GPIO_SetBits(GPIOB, GPIO_Pin_5);
			   GPIO_SetBits(GPIOB, GPIO_Pin_6);
			   GPIO_SetBits(GPIOB, GPIO_Pin_7);
		//	   GPIO_SetBits(GPIOB, GPIO_Pin_12);
		break;
	case 2:
		  GPIO_SetBits(GPIOD, GPIO_Pin_0);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_2);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_3);
			   GPIO_SetBits(GPIOB, GPIO_Pin_8);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_5);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_6);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_7);
			//   GPIO_SetBits(GPIOB, GPIO_Pin_12);

		break;
	case 3:
		  GPIO_SetBits(GPIOD, GPIO_Pin_0);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_2);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_3);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_8);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_5);
			   GPIO_SetBits(GPIOB, GPIO_Pin_6);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_7);
			  // GPIO_SetBits(GPIOB, GPIO_Pin_12);
		break;
	case 4:
		  GPIO_ResetBits(GPIOD, GPIO_Pin_0);
			   GPIO_SetBits(GPIOD, GPIO_Pin_2);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_3);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_8);
			   GPIO_SetBits(GPIOB, GPIO_Pin_5);
			   GPIO_SetBits(GPIOB, GPIO_Pin_6);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_7);
			   //GPIO_SetBits(GPIOB, GPIO_Pin_12);
		break;
	case 5:

		  GPIO_ResetBits(GPIOD, GPIO_Pin_0);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_2);
			   GPIO_SetBits(GPIOD, GPIO_Pin_3);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_8);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_5);
			   GPIO_SetBits(GPIOB, GPIO_Pin_6);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_7);
			   //GPIO_SetBits(GPIOB, GPIO_Pin_12);
		break;
	case 6:

		  GPIO_ResetBits(GPIOD, GPIO_Pin_0);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_2);
			   GPIO_SetBits(GPIOD, GPIO_Pin_3);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_8);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_5);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_6);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_7);
			  // GPIO_SetBits(GPIOB, GPIO_Pin_12);
		break;
	case 7:

		  GPIO_SetBits(GPIOD, GPIO_Pin_0);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_2);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_3);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_8);
			   GPIO_SetBits(GPIOB, GPIO_Pin_5);
			   GPIO_SetBits(GPIOB, GPIO_Pin_6);
			   GPIO_SetBits(GPIOB, GPIO_Pin_7);
			   //GPIO_SetBits(GPIOB, GPIO_Pin_12);
		break;
	case 8:
		  GPIO_ResetBits(GPIOD, GPIO_Pin_0);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_2);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_3);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_8);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_5);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_6);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_7);
			   //GPIO_SetBits(GPIOB, GPIO_Pin_12);
		break;
	case 9:
		  GPIO_ResetBits(GPIOD, GPIO_Pin_0);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_2);
			   GPIO_ResetBits(GPIOD, GPIO_Pin_3);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_8);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_5);
			   GPIO_SetBits(GPIOB, GPIO_Pin_6);
			   GPIO_ResetBits(GPIOB, GPIO_Pin_7);
			  // GPIO_SetBits(GPIOB, GPIO_Pin_12);
		break;
	case 13:
	GPIO_ResetBits(GPIOD, GPIO_Pin_0);
	GPIO_ResetBits(GPIOD, GPIO_Pin_2);
	GPIO_SetBits(GPIOD, GPIO_Pin_3);
	GPIO_SetBits(GPIOB, GPIO_Pin_8);
	GPIO_ResetBits(GPIOB, GPIO_Pin_5);
	GPIO_ResetBits(GPIOB, GPIO_Pin_6);
	GPIO_SetBits(GPIOB, GPIO_Pin_7);
	break ;
	case 12:
		GPIO_ResetBits(GPIOD, GPIO_Pin_0);
	    GPIO_ResetBits(GPIOD, GPIO_Pin_2);
	    GPIO_ResetBits(GPIOD, GPIO_Pin_3);
        GPIO_SetBits(GPIOB, GPIO_Pin_8);
        GPIO_SetBits(GPIOB, GPIO_Pin_5);
		GPIO_SetBits(GPIOB, GPIO_Pin_6);
	    GPIO_ResetBits(GPIOB, GPIO_Pin_7);
break;
	}
}
uint8_t readADC() {
	ADC_RegularChannelConfig(ADC1, ADC_Channel_8, 1, ADC_SampleTime_56Cycles);
	ADC_SoftwareStartConv(ADC1);
	while (ADC_GetFlagStatus(ADC1, ADC_FLAG_EOC) == RESET)
		;
	return ADC_GetConversionValue(ADC1);
}

int main(void) {
int i , k , j ;

	init();


	uint8_t value = 0;
		GPIO_InitTypeDef GPIO_InitStructure;
		ADC_InitTypeDef ADC_InitStructre;
		ADC_CommonInitTypeDef ADC_CommonInitStructure;

		RCC_APB2PeriphClockCmd(RCC_APB2Periph_ADC1, ENABLE);
		RCC_AHB1PeriphClockCmd(RCC_AHB1Periph_GPIOA | RCC_AHB1Periph_GPIOB, ENABLE);
		RCC_AHB1PeriphClockCmd(RCC_AHB1Periph_GPIOD, ENABLE);

	 

		GPIO_InitStructure.GPIO_Pin = GPIO_Pin_0;
		GPIO_InitStructure.GPIO_Mode = GPIO_Mode_AN; //Mode analogique du PIN
		GPIO_InitStructure.GPIO_PuPd = GPIO_PuPd_NOPULL; // Pas de résistances de PULL-UP PULL-DOWN
		GPIO_Init(GPIOB, &GPIO_InitStructure);

		ADC_CommonInitStructure.ADC_Mode = ADC_Mode_Independent; // Pas d'ADC complémentaire
		ADC_CommonInitStructure.ADC_Prescaler = ADC_Prescaler_Div4; //Division du signal d'horloge pour respecter le thèoreme
		ADC_CommonInitStructure.ADC_DMAAccessMode = ADC_DMAAccessMode_Disabled; //DMA désactivé
		ADC_CommonInitStructure.ADC_TwoSamplingDelay = ADC_TwoSamplingDelay_5Cycles;
		ADC_CommonStructInit(&ADC_CommonInitStructure);

		ADC_InitStructre.ADC_ContinuousConvMode = DISABLE; // Conversion sur un seul échantillon
		ADC_InitStructre.ADC_ScanConvMode = DISABLE; // Conversion à partir de la config déclaré
		ADC_InitStructre.ADC_Resolution = ADC_Resolution_8b; // Résolution de l'ADC
		ADC_InitStructre.ADC_ExternalTrigConv = ADC_ExternalTrigConvEdge_None; // Pas de trigger Externe
		ADC_InitStructre.ADC_DataAlign = ADC_DataAlign_Right; // Résultat stocké dans le bit le plus signifiant droit
		ADC_InitStructre.ADC_NbrOfConversion = 1; // Un seul ADC et un seul channel
		ADC_Init(ADC1, &ADC_InitStructre);
		ADC_Cmd(ADC1, ENABLE); //Init ADC

		 

		double temperature;





	while (1) {
		value = readADC();

				temperature = value;
				i = (int) temperature  ;

		for (j = 0; j < (100); j++) {

			GPIO_SetBits(GPIOB, GPIO_Pin_14);

					ecrire(13);
					for (k = 0; k < (11000); k++)
								;
					GPIO_ResetBits(GPIOB, GPIO_Pin_14);

			        GPIO_SetBits(GPIOB, GPIO_Pin_12);

					ecrire(12);
					for (k = 0; k < (11000); k++)
						;
					GPIO_ResetBits(GPIOB, GPIO_Pin_12);



        	 GPIO_SetBits(GPIOB, GPIO_Pin_13);
		ecrire(i % 10);

		for (k = 0; k < (11000); k++)
			;
		GPIO_ResetBits(GPIOB, GPIO_Pin_13);


        GPIO_SetBits(GPIOB, GPIO_Pin_11);

		ecrire(i / 10);
		for (k = 0; k < (11000); k++)
			;

		GPIO_ResetBits(GPIOB, GPIO_Pin_11);


		}
	}
	}


/*
 * Callback used by stm32f4_discovery_audio_codec.c.
 * Refer to stm32f4_discovery_audio_codec.h for more info.
 */
void EVAL_AUDIO_TransferComplete_CallBack(uint32_t pBuffer, uint32_t Size) {
	/* TODO, implement your code here */
	return;
}

/*
 * Callback used by stm324xg_eval_audio_codec.c.

 * Refer to stm324xg_eval_audio_codec.h for more info.
 */
uint16_t EVAL_AUDIO_GetSampleCallBack(void) {
	/* TODO, implement your code here */
	return -1;

}

