int salario_base, salario_min = 1412, horas;
    float aux_alim = 0, aux_trans = 0, aux_cre = 0, aux_esc = 0, aux_creche = 0, seg_vi = 0, aux_sau = 0;
    float salario_liquido;

    printf("Digite o salario base: ");
    scanf("%d", &salario_base);

    if (salario_base < salario_min) {
        printf("O valor é inválido\n");
        return 1;
    }

    printf("Digite a carga horária semanal: \n");
    scanf("%d", &horas);

    if (horas < 30) {
        aux_alim = 0;
    } else if (horas == 30) {
        aux_alim = 286;
    } else if (horas == 40) {
        aux_alim = 440;
    }


    int psd;
    float p;

    printf("Digite o número de passagens por dia: \n");
    scanf("%d", &psd);
    printf("Digite o valor da passagem: \n");
    scanf("%f", &p);

    int dias_uteis = 22;
    aux_trans = psd * p * dias_uteis;

    
    int resposta;
    float valor_ofe;
    printf("A empresa oferece auxilio educação? \n");
    printf("Digite 1 para sim e 0 para não: \n");
    scanf("%d", &resposta);

    if (resposta == 1) {
        printf("Digite o valor oferecido pela empresa: \n");
        scanf("%f", &valor_ofe);
        aux_esc = valor_ofe;
    }

    
    printf("A empresa oferece auxilio saude? \n");
    printf("Digite 1 para sim e 0 para não: \n");
    scanf("%d", &resposta);

    if (resposta == 1) {
        printf("Digite o valor oferecido pela empresa: \n");
        scanf("%f", &valor_ofe);
        aux_sau = valor_ofe;
    }

   
    printf("A empresa oferece auxilio creche e você tem um filho de até 6 anos? \n");
    printf("Digite 1 para sim e 0 para não: \n");
    scanf("%d", &resposta);

    if (resposta == 1) {
        aux_creche = salario_base * 0.05;
    }

   
    printf("A empresa oferece seguro de vida? \n");
    printf("Digite 1 para sim e 0 para não: \n");
    scanf("%d", &resposta);

    if (resposta == 1) {
        printf("Digite o valor oferecido pela empresa: \n");
        scanf("%f", &valor_ofe);
        seg_vi = valor_ofe;
    }

    
    float irpf;
    float inss;
    float fgts = salario_base * 0.08;
    float cont_sind = salario_base / 30; 

    if (salario_base <= 2112.00) {
        inss = salario_base * 0.075;
    } else if (salario_base <= 2666.68) {
        inss = salario_base * 0.09;
    } else if (salario_base <= 4000.03) {
        inss = salario_base * 0.12;
    } else if (salario_base <= 7786.02) {
        inss = salario_base * 0.14;
    } else {
        inss = 7786.02 * 0.14; 
    }

    if (salario_base <= 2112.00) {
        irpf = 0;
    } else if (salario_base <= 2826.66) {
        irpf = salario_base * 0.075;
    } else if (salario_base <= 3751.06) {
        irpf = salario_base * 0.15;
    } else if (salario_base <= 4664.68) {
        irpf = salario_base * 0.225;
    } else {
        irpf = salario_base * 0.275;
    }

    salario_liquido = salario_base - (irpf + inss + fgts + cont_sind + aux_trans + aux_creche + seg_vi) + aux_esc + aux_alim + aux_sau;

    printf("O salario liquido é: %.2f\n", salario_liquido);

    return 0;
}
