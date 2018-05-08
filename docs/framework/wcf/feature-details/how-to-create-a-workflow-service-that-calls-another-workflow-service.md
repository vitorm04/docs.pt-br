---
title: Como criar um serviço de fluxo de trabalho que chama outro serviço de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: fda5a7286c3d20c7cdc2093e58bfe3fbdcf1d1c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a>Como criar um serviço de fluxo de trabalho que chama outro serviço de fluxo de trabalho
Às vezes, é necessário para um serviço de fluxo de trabalho obter informações de outro serviço de fluxo de trabalho.  Este tópico demonstra como chamar um serviço de fluxo de trabalho de outro. Neste tópico, vamos criar dois serviços de fluxo de trabalho; um que tenha um método que reverte a cadeia de caracteres de entrada e outra que converte a cadeia de caracteres de entrada em maiusculas depois de reverter a cadeia de caracteres que usa o serviço primeiro.  
  
### <a name="to-create-the-reverser-workflow-service"></a>Para criar o serviço de fluxo de trabalho reversor  
  
1.  Execução [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] como um administrador.  
  
2.  Selecione **arquivo**, **novo projeto**. Sob o **fluxo de trabalho** nó o **modelos instalados** painel, selecione **aplicativo de serviço de fluxo de trabalho WCF**. Nome da solução `NestedServices` e, em seguida, clique em **Okey**.  
  
3.  Em **servidores**, certifique-se de que **usar servidor Web do IIS Local** é selecionado. Clique em **criar o diretório Virtual**. Clique em **Okey** em que a caixa de diálogo informando que o diretório virtual foi criado com êxito.  
  
4.  No Solution Explorer, renomeie Service1.xamlx para `StringReverserService.xamlx`.  
  
5.  Sobre o **propriedades do projeto** para o novo projeto, clique no **Web** guia. Definir o **iniciar ação** para **página específica**e selecione StringReverserService.xamlx como a página para iniciar.  
  
6.  Abra StringReverserService.xamlx no designer e exclua o existente `ReceiveRequest` e `SendReply` atividades e, em seguida, arraste um `ReceiveAndSendReply` atividade para a atividade de sequência existente.  
  
    1.  Definir o **OperationName** para ReverseString.  
  
    2.  Definir o **ServiceContractName** para IReverseString.  
  
    3.  Selecione o **CanCreateInstance** caixa de seleção.  
  
7.  Selecione o **SequentialService** atividade e, em seguida, clique o **variáveis** guia na parte inferior do designer. Crie duas novas variáveis nomeadas StringToReverse e ReversedStringToReturn do tipo cadeia de caracteres.  
  
8.  Clique o **definir** link no **Receive** atividade. Clique o **parâmetros**e crie um parâmetro denominado InputString do tipo cadeia de caracteres que atribui a StringToReverse.  
  
9. Clique o **definir** link no **SendReplyToReceive** atividade. Clique o **parâmetros**e crie um parâmetro denominado ReversedString do tipo cadeia de caracteres, atribuído a ReversedStringToReturn.  
  
10. Para implementar a lógica para o serviço, crie uma nova classe no projeto chamado StringLibrary.  Substitua a definição de classe com o código a seguir.  
  
    ```  
    public class StringLibrary  
        {  
            public static String ReverseString(string StringToReverse)  
            {  
                char[] charArray = StringToReverse.ToCharArray();  
                Array.Reverse(charArray);  
                return new String(charArray);  
            }  
        }  
    ```  
  
11. Para chamar o método ReverseString na entrada, arraste um **InvokeMethod** atividade da caixa de ferramentas para o espaço entre o **Receive** e **SendReply** atividades. Defina as propriedades da atividade da seguinte maneira:  
  
    1.  **MethodName**: ReverseString  
  
    2.  **Resultado**: ReversedStringToReturn  
  
    3.  **Parâmetros**: criar um novo parâmetro com um **direção** no, um **tipo** de cadeia de caracteres e um **valor** de StringToReverse.  
  
    4.  **TargetType**: NestedServices.StringLibrary  
  
12. Teste o serviço pressionando F5. No cliente de teste de WCF é exibida, clique duas vezes o método ReverseString(). No painel de solicitação, digite `Sample` para o valor do parâmetro InputString. Clique em **invocar**. O serviço deve retornar "elpmaS".  
  
### <a name="to-create-the-uppercaser-workflow-service"></a>Para criar o serviço de fluxo de trabalho UpperCaser  
  
1.  O projeto NestedServices e selecione **adicionar**, **Novo Item**. No **fluxo de trabalho** nó, selecione **serviço de fluxo de trabalho WCF**e nomeie o novo serviço `UpperCaserService`. Clique em **Adicionar**. Isso deve adicionar um novo serviço de fluxo de trabalho chamado UpperCaserService.xamlx ao projeto.  
  
2.  Abra UpperCaserService.xamlx no designer e exclua o existente **ReceiveRequest** e `SendReply` atividades e arraste um `ReceiveAndSendReply` atividade para a atividade de sequência existente.  
  
    1.  Definir o **OperationName** para UpperCaseString.  
  
    2.  Definir o **ServiceContractName** para IUpperCaseString.  
  
    3.  Selecione o **CanCreateInstance** caixa de seleção.  
  
3.  Selecione a atividade de SequentialService e, em seguida, clique no **variáveis** guia na parte inferior do designer. Crie três novas variáveis nomeadas StringToUpper, StringToReverse e StringToReturn do tipo cadeia de caracteres.  
  
4.  Clique o **definir** link no **Receive** atividade. Clique o **parâmetros**e crie um parâmetro denominado InputString do tipo cadeia de caracteres que atribui a StringToUpper.  
  
5.  Clique o **definir** link no **SendReplyToReceive** atividade. Clique o **parâmetros**e crie um parâmetro denominado ModifiedString do tipo cadeia de caracteres, atribuído a StringToReturn.  
  
6.  Para implementar a lógica para o serviço, crie um novo método na classe StringLibrary usando o código a seguir.  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
    ```  
  
7.  Para chamar o método UpperCaseString na entrada, arraste um **InvokeMethod** atividade da caixa de ferramentas para o espaço entre o **Receive** e **SendReply** atividades. Defina as propriedades da atividade da seguinte maneira:  
  
    1.  **MethodName**: UpperCaseString  
  
    2.  **Resultado**: StringToReverse  
  
    3.  **Parâmetros**: criar um novo parâmetro com um **direção** no, um **tipo** de cadeia de caracteres e um **valor** de StringToUpper.  
  
    4.  **TargetType**: NestedServices.StringLibrary  
  
8.  Agora, chamaremos o primeiro serviço na cadeia de caracteres modificada. Clique com o botão direito e selecione **adicionar referência de serviço**. Adicionar uma referência de serviço para o serviço em http://localhost/NestedServices/StringReverserService.xamlx e compilar o projeto para criar uma atividade personalizada para acessar o primeiro serviço Web.  
  
9. Arraste uma instância da nova atividade de fluxo de trabalho, entre o **InvokeMethod** atividade e o **SendReplyToReceive** atividades. Atribua a variável StringToReverse à propriedade InputString da nova atividade e a variável StringToReturn à propriedade StringToReturn.  
  
10. Abra a página de propriedades para o projeto NestedServices e altere o **página específica** no **Web** tab para UpperCaserService.xamlx.  
  
11. Teste o serviço pressionando F5. No cliente de teste de WCF é exibida, clique duas vezes o método ReverseString(). No painel de solicitação, digite `Sample` para o valor do parâmetro InputString. Clique em **invocar**. O serviço deve retornar "ELPMAS".  
  
### <a name="to-create-a-client-to-call-the-services"></a>Para criar um cliente para chamar os serviços  
  
1.  Adicione um novo projeto de aplicativo de Console chamado cliente para a solução.  
  
2.  O projeto de cliente e selecione **adicionar referência de serviço**. Na janela que aparece, clique em **Discover**. Selecione StringReverserService.xamlx e, em seguida, digite ReverseService como o namespace.  Clique em **OK**.  
  
3.  Substitua o método Main em Program.cs pelo código a seguir.  
  
    ```  
    static void Main(string[] args)  
    {  
        Console.Write("Input string to process:");  
        String input = Console.ReadLine();  
        var service = new ReverseService.ReverseStringClient();  
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));  
        Console.ReadKey();  
    }  
    ```
