Calculator

using System;

class Calculadora
{
    static void Main()
    {
        while (true)
        {
            MostrarCaixaSuperior();
            Console.WriteLine("Calculadora");
            MostrarCaixaInferior();

            MostrarOpcoes();

            int escolha;
            if (int.TryParse(Console.ReadLine(), out escolha))
            {
                if (escolha == 0)
                {
                    Console.WriteLine("|          Saindo           |");
                    MostrarCaixaInferior();
                    break;
                }

                double resultado = ExecutarOperacao(escolha);
                Console.WriteLine($"|   Resultado: {resultado,-23}|");
            }
            else
            {
                Console.WriteLine("| Escolha inválida. Tente novamente. |");
            }

            MostrarCaixaInferior();
        }
    }

    static void MostrarOpcoes()
    {
        Console.WriteLine("| Escolha a operação:       |");
        Console.WriteLine("| 1 - Soma                  |");
        Console.WriteLine("| 2 - Subtração             |");
        Console.WriteLine("| 3 - Multiplicação         |");
        Console.WriteLine("| 4 - Divisão               |");
        Console.WriteLine("| 5 - Porcentagem           |");
        Console.WriteLine("| 6 - Frações               |");
        Console.WriteLine("| 0 - Sair                  |");
    }

    static double ExecutarOperacao(int escolha)
    {
        double resultado = 0;

        switch (escolha)
        {
            case 1:
                resultado = Soma();
                break;
            case 2:
                resultado = Subtracao();
                break;
            case 3:
                resultado = Multiplicacao();
                break;
            case 4:
                resultado = Divisao();
                break;
            case 5:
                resultado = Porcentagem();
                break;
            case 6:
                resultado = Fracoes();
                break;
            default:
                Console.WriteLine("| Escolha inválida. Tente novamente. |");
                break;
        }

        return resultado;
    }

    static double Soma()
    {
        return ObterNumero("| Digite o primeiro número:") + ObterNumero("| Digite o segundo número: ");
    }

    static double Subtracao()
    {
        return ObterNumero("| Digite o primeiro número:") - ObterNumero("| Digite o segundo número: ");
    }

    static double Multiplicacao()
    {
        return ObterNumero("| Digite o primeiro número:") * ObterNumero("| Digite o segundo número: ");
    }

    static double Divisao()
    {
        double numerador = ObterNumero("| Digite o numerador:        ");
        double denominador;

        do
        {
            denominador = ObterNumero("| Digite o denominador (não pode ser zero):");
        } while (denominador == 0);

        return numerador / denominador;
    }

    static double Porcentagem()
    {
        double valor = ObterNumero("| Digite o valor:            ");
        double porcentagem = ObterNumero("| Digite a porcentagem:      ");

        return (valor * porcentagem) / 100;
    }

    static double Fracoes()
    {
        double numerador = ObterNumero("| Digite o numerador:        ");
        double denominador;

        do
        {
            denominador = ObterNumero("| Digite o denominador (não pode ser zero):");
        } while (denominador == 0);

        return numerador / denominador;
    }

    static double ObterNumero(string mensagem)
    {
        double numero;
        do
        {
            Console.WriteLine(mensagem);
        } while (!double.TryParse(Console.ReadLine(), out numero));

        return numero;
    }

    static void MostrarCaixaSuperior()
    {
        Console.WriteLine("-----------------------------");
    }

    static void MostrarCaixaInferior()
    {
        Console.WriteLine("-----------------------------");
    }
}
