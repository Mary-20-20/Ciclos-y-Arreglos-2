# Ciclos-y-Arreglos-2
SEGUNDO PUNTO DE "CICLOS Y ARREGLOS"

#include<stdio.h>


float calcularMC(float peso, float estatura) {
    return peso / (estatura * estatura);
}
float calcularPI (float PI, float estatura){
    return PI * (estatura * estatura);
}

int main() {

    int personas;

    printf("digite el numero de personas: ");
    scanf("%i",&personas);


    float peso[personas];
    float estatura[personas];
    float MC[personas];

    int delgado = 0;
    int normal = 0;
    int sobrepeso = 0;



    for (int contador=0; contador < personas; contador++){
        printf("persona. %i\n", contador +1);
        printf("cual es su peso en kg: ");
        scanf("%f",&peso [contador]);
        printf("digite la estatura en metros: ");
        scanf("%f",&estatura[contador]);

        MC[contador] = calcularMC(peso[contador], estatura[contador]);

        if (MC[contador] < 18.5){
            delgado++;
            float PI = calcularPI(18.5, estatura[contador]);
            printf("para que su peso de acuerdo a su estatura este en un rango normal,su peso ideal es de: minimo %.2f kg y maximo %.2f kg \n", calcularPI(18.5, estatura[contador]), calcularPI(24.9,estatura[contador]));
        }else if (MC [contador] >= 18.5 && MC [contador]<=24.9){
            normal++;
            printf("usted se encuentra dentro de su peso ideal\n");
        }else{
            sobrepeso++;
            float PI = calcularPI(estatura[contador], 24.9);
            printf("para que su peso sea ideal teniendo en cuenta su estatura, su peso debe estar entre %.2f kg y %.2fkg\n", calcularPI(18.5, estatura[contador]), calcularPI(24.9,estatura[contador]));
        }
    }


    printf("la MC de cada persona es:\n");

    for (int contador=0; contador < personas; contador++){
        printf("persona %i: MC = %.2f\n", contador + 1, MC[contador]);
    }

    printf("\nporcentajes:\n");
    printf("porcentaje con delgadez: %.2f%%\n",(delgado * 100.0)/personas);
    printf("porcentaje de normales: %.2f%%\n", (normal * 100.0) / personas);
    printf("porcentaje de sobrepeso: %.2f%%\n", (sobrepeso * 100.0 / personas));


    return 0;
}
