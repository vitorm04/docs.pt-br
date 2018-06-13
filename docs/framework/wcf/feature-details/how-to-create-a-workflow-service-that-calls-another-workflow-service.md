---
title: Como criar um serviço de fluxo de trabalho que chama outro serviço de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: fda5a7286c3d20c7cdc2093e58bfe3fbdcf1d1c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497185"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a><span data-ttu-id="8de78-102">Como criar um serviço de fluxo de trabalho que chama outro serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="8de78-102">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>
<span data-ttu-id="8de78-103">Às vezes, é necessário para um serviço de fluxo de trabalho obter informações de outro serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8de78-103">It is sometimes necessary for a workflow service to obtain information from another workflow service.</span></span>  <span data-ttu-id="8de78-104">Este tópico demonstra como chamar um serviço de fluxo de trabalho de outro.</span><span class="sxs-lookup"><span data-stu-id="8de78-104">This topic demonstrates how to call one workflow service from another.</span></span> <span data-ttu-id="8de78-105">Neste tópico, vamos criar dois serviços de fluxo de trabalho; um que tenha um método que reverte a cadeia de caracteres de entrada e outra que converte a cadeia de caracteres de entrada em maiusculas depois de reverter a cadeia de caracteres que usa o serviço primeiro.</span><span class="sxs-lookup"><span data-stu-id="8de78-105">In this topic, we’ll create two workflow services; one that has a method that reverses the input string, and another that converts the input string to uppercase after reversing the string that uses the first service.</span></span>  
  
### <a name="to-create-the-reverser-workflow-service"></a><span data-ttu-id="8de78-106">Para criar o serviço de fluxo de trabalho reversor</span><span class="sxs-lookup"><span data-stu-id="8de78-106">To create the Reverser workflow service</span></span>  
  
1.  <span data-ttu-id="8de78-107">Execução [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] como um administrador.</span><span class="sxs-lookup"><span data-stu-id="8de78-107">Run [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] as an administrator.</span></span>  
  
2.  <span data-ttu-id="8de78-108">Selecione **arquivo**, **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="8de78-108">Select **File**, **New Project**.</span></span> <span data-ttu-id="8de78-109">Sob o **fluxo de trabalho** nó o **modelos instalados** painel, selecione **aplicativo de serviço de fluxo de trabalho WCF**.</span><span class="sxs-lookup"><span data-stu-id="8de78-109">Under the **Workflow** node in the **Installed Templates** pane, select **WCF Workflow Service Application**.</span></span> <span data-ttu-id="8de78-110">Nome da solução `NestedServices` e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="8de78-110">Name the solution `NestedServices` and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="8de78-111">Em **servidores**, certifique-se de que **usar servidor Web do IIS Local** é selecionado.</span><span class="sxs-lookup"><span data-stu-id="8de78-111">Under **Servers**, make sure that **Use Local IIS Web Server** is selected.</span></span> <span data-ttu-id="8de78-112">Clique em **criar o diretório Virtual**.</span><span class="sxs-lookup"><span data-stu-id="8de78-112">Click **Create Virtual Directory**.</span></span> <span data-ttu-id="8de78-113">Clique em **Okey** em que a caixa de diálogo informando que o diretório virtual foi criado com êxito.</span><span class="sxs-lookup"><span data-stu-id="8de78-113">Click **OK** in the dialog box stating that the virtual directory was successfully created.</span></span>  
  
4.  <span data-ttu-id="8de78-114">No Solution Explorer, renomeie Service1.xamlx para `StringReverserService.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="8de78-114">In Solution Explorer, rename Service1.xamlx to `StringReverserService.xamlx`.</span></span>  
  
5.  <span data-ttu-id="8de78-115">Sobre o **propriedades do projeto** para o novo projeto, clique no **Web** guia. Definir o **iniciar ação** para **página específica**e selecione StringReverserService.xamlx como a página para iniciar.</span><span class="sxs-lookup"><span data-stu-id="8de78-115">On the **Project Properties** page for the new project, click the **Web** tab. Set the **Start Action** to **Specific Page**, and select StringReverserService.xamlx as the page to start.</span></span>  
  
6.  <span data-ttu-id="8de78-116">Abra StringReverserService.xamlx no designer e exclua o existente `ReceiveRequest` e `SendReply` atividades e, em seguida, arraste um `ReceiveAndSendReply` atividade para a atividade de sequência existente.</span><span class="sxs-lookup"><span data-stu-id="8de78-116">Open StringReverserService.xamlx in the designer and delete the existing `ReceiveRequest` and `SendReply` activities, and then drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>  
  
    1.  <span data-ttu-id="8de78-117">Definir o **OperationName** para ReverseString.</span><span class="sxs-lookup"><span data-stu-id="8de78-117">Set the **OperationName** to ReverseString.</span></span>  
  
    2.  <span data-ttu-id="8de78-118">Definir o **ServiceContractName** para IReverseString.</span><span class="sxs-lookup"><span data-stu-id="8de78-118">Set the **ServiceContractName** to IReverseString.</span></span>  
  
    3.  <span data-ttu-id="8de78-119">Selecione o **CanCreateInstance** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="8de78-119">Select the **CanCreateInstance** check box.</span></span>  
  
7.  <span data-ttu-id="8de78-120">Selecione o **SequentialService** atividade e, em seguida, clique o **variáveis** guia na parte inferior do designer.</span><span class="sxs-lookup"><span data-stu-id="8de78-120">Select the **SequentialService** activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="8de78-121">Crie duas novas variáveis nomeadas StringToReverse e ReversedStringToReturn do tipo cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8de78-121">Create two new variables named StringToReverse and ReversedStringToReturn of type String.</span></span>  
  
8.  <span data-ttu-id="8de78-122">Clique o **definir** link no **Receive** atividade.</span><span class="sxs-lookup"><span data-stu-id="8de78-122">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="8de78-123">Clique o **parâmetros**e crie um parâmetro denominado InputString do tipo cadeia de caracteres que atribui a StringToReverse.</span><span class="sxs-lookup"><span data-stu-id="8de78-123">Click the  **Parameters**, and create a parameter named InputString of type String that assigns to StringToReverse.</span></span>  
  
9. <span data-ttu-id="8de78-124">Clique o **definir** link no **SendReplyToReceive** atividade.</span><span class="sxs-lookup"><span data-stu-id="8de78-124">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="8de78-125">Clique o **parâmetros**e crie um parâmetro denominado ReversedString do tipo cadeia de caracteres, atribuído a ReversedStringToReturn.</span><span class="sxs-lookup"><span data-stu-id="8de78-125">Click the **Parameters**, and create a parameter named ReversedString of type String, assigned to ReversedStringToReturn.</span></span>  
  
10. <span data-ttu-id="8de78-126">Para implementar a lógica para o serviço, crie uma nova classe no projeto chamado StringLibrary.</span><span class="sxs-lookup"><span data-stu-id="8de78-126">To implement the logic for the service, create a new class in the project called StringLibrary.</span></span>  <span data-ttu-id="8de78-127">Substitua a definição de classe com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8de78-127">Replace the class definition with the following code.</span></span>  
  
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
  
11. <span data-ttu-id="8de78-128">Para chamar o método ReverseString na entrada, arraste um **InvokeMethod** atividade da caixa de ferramentas para o espaço entre o **Receive** e **SendReply** atividades.</span><span class="sxs-lookup"><span data-stu-id="8de78-128">To call the ReverseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="8de78-129">Defina as propriedades da atividade da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8de78-129">Set the properties of the activity as follows:</span></span>  
  
    1.  <span data-ttu-id="8de78-130">**MethodName**: ReverseString</span><span class="sxs-lookup"><span data-stu-id="8de78-130">**MethodName**: ReverseString</span></span>  
  
    2.  <span data-ttu-id="8de78-131">**Resultado**: ReversedStringToReturn</span><span class="sxs-lookup"><span data-stu-id="8de78-131">**Result**: ReversedStringToReturn</span></span>  
  
    3.  <span data-ttu-id="8de78-132">**Parâmetros**: criar um novo parâmetro com um **direção** no, um **tipo** de cadeia de caracteres e um **valor** de StringToReverse.</span><span class="sxs-lookup"><span data-stu-id="8de78-132">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToReverse.</span></span>  
  
    4.  <span data-ttu-id="8de78-133">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="8de78-133">**TargetType**: NestedServices.StringLibrary</span></span>  
  
12. <span data-ttu-id="8de78-134">Teste o serviço pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="8de78-134">Test the service by pressing F5.</span></span> <span data-ttu-id="8de78-135">No cliente de teste de WCF é exibida, clique duas vezes o método ReverseString().</span><span class="sxs-lookup"><span data-stu-id="8de78-135">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="8de78-136">No painel de solicitação, digite `Sample` para o valor do parâmetro InputString.</span><span class="sxs-lookup"><span data-stu-id="8de78-136">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="8de78-137">Clique em **invocar**.</span><span class="sxs-lookup"><span data-stu-id="8de78-137">Click **Invoke**.</span></span> <span data-ttu-id="8de78-138">O serviço deve retornar "elpmaS".</span><span class="sxs-lookup"><span data-stu-id="8de78-138">The service should return "elpmaS".</span></span>  
  
### <a name="to-create-the-uppercaser-workflow-service"></a><span data-ttu-id="8de78-139">Para criar o serviço de fluxo de trabalho UpperCaser</span><span class="sxs-lookup"><span data-stu-id="8de78-139">To create the UpperCaser workflow service</span></span>  
  
1.  <span data-ttu-id="8de78-140">O projeto NestedServices e selecione **adicionar**, **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="8de78-140">Right-click the NestedServices project and select **Add**, **New Item**.</span></span> <span data-ttu-id="8de78-141">No **fluxo de trabalho** nó, selecione **serviço de fluxo de trabalho WCF**e nomeie o novo serviço `UpperCaserService`.</span><span class="sxs-lookup"><span data-stu-id="8de78-141">In the **Workflow** node, select **WCF Workflow Service**, and name the new service `UpperCaserService`.</span></span> <span data-ttu-id="8de78-142">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="8de78-142">Click **Add**.</span></span> <span data-ttu-id="8de78-143">Isso deve adicionar um novo serviço de fluxo de trabalho chamado UpperCaserService.xamlx ao projeto.</span><span class="sxs-lookup"><span data-stu-id="8de78-143">This should add a new workflow service called UpperCaserService.xamlx to the project.</span></span>  
  
2.  <span data-ttu-id="8de78-144">Abra UpperCaserService.xamlx no designer e exclua o existente **ReceiveRequest** e `SendReply` atividades e arraste um `ReceiveAndSendReply` atividade para a atividade de sequência existente.</span><span class="sxs-lookup"><span data-stu-id="8de78-144">Open UpperCaserService.xamlx in the designer and delete the existing **ReceiveRequest** and `SendReply` activities, and drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>  
  
    1.  <span data-ttu-id="8de78-145">Definir o **OperationName** para UpperCaseString.</span><span class="sxs-lookup"><span data-stu-id="8de78-145">Set the **OperationName** to UpperCaseString.</span></span>  
  
    2.  <span data-ttu-id="8de78-146">Definir o **ServiceContractName** para IUpperCaseString.</span><span class="sxs-lookup"><span data-stu-id="8de78-146">Set the **ServiceContractName** to IUpperCaseString.</span></span>  
  
    3.  <span data-ttu-id="8de78-147">Selecione o **CanCreateInstance** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="8de78-147">Select the **CanCreateInstance** check box.</span></span>  
  
3.  <span data-ttu-id="8de78-148">Selecione a atividade de SequentialService e, em seguida, clique no **variáveis** guia na parte inferior do designer.</span><span class="sxs-lookup"><span data-stu-id="8de78-148">Select the SequentialService activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="8de78-149">Crie três novas variáveis nomeadas StringToUpper, StringToReverse e StringToReturn do tipo cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8de78-149">Create three new variables named StringToUpper, StringToReverse, and StringToReturn of type String.</span></span>  
  
4.  <span data-ttu-id="8de78-150">Clique o **definir** link no **Receive** atividade.</span><span class="sxs-lookup"><span data-stu-id="8de78-150">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="8de78-151">Clique o **parâmetros**e crie um parâmetro denominado InputString do tipo cadeia de caracteres que atribui a StringToUpper.</span><span class="sxs-lookup"><span data-stu-id="8de78-151">Click the **Parameters**, and create a parameter named InputString of type String that assigns to StringToUpper.</span></span>  
  
5.  <span data-ttu-id="8de78-152">Clique o **definir** link no **SendReplyToReceive** atividade.</span><span class="sxs-lookup"><span data-stu-id="8de78-152">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="8de78-153">Clique o **parâmetros**e crie um parâmetro denominado ModifiedString do tipo cadeia de caracteres, atribuído a StringToReturn.</span><span class="sxs-lookup"><span data-stu-id="8de78-153">Click the **Parameters**, and create a parameter named ModifiedString of type String, assigned to StringToReturn.</span></span>  
  
6.  <span data-ttu-id="8de78-154">Para implementar a lógica para o serviço, crie um novo método na classe StringLibrary usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8de78-154">To implement the logic for the service, create a new method in the StringLibrary class using the following code.</span></span>  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
    ```  
  
7.  <span data-ttu-id="8de78-155">Para chamar o método UpperCaseString na entrada, arraste um **InvokeMethod** atividade da caixa de ferramentas para o espaço entre o **Receive** e **SendReply** atividades.</span><span class="sxs-lookup"><span data-stu-id="8de78-155">To call the UpperCaseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="8de78-156">Defina as propriedades da atividade da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8de78-156">Set the properties of the activity as follows:</span></span>  
  
    1.  <span data-ttu-id="8de78-157">**MethodName**: UpperCaseString</span><span class="sxs-lookup"><span data-stu-id="8de78-157">**MethodName**: UpperCaseString</span></span>  
  
    2.  <span data-ttu-id="8de78-158">**Resultado**: StringToReverse</span><span class="sxs-lookup"><span data-stu-id="8de78-158">**Result**: StringToReverse</span></span>  
  
    3.  <span data-ttu-id="8de78-159">**Parâmetros**: criar um novo parâmetro com um **direção** no, um **tipo** de cadeia de caracteres e um **valor** de StringToUpper.</span><span class="sxs-lookup"><span data-stu-id="8de78-159">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToUpper.</span></span>  
  
    4.  <span data-ttu-id="8de78-160">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="8de78-160">**TargetType**: NestedServices.StringLibrary</span></span>  
  
8.  <span data-ttu-id="8de78-161">Agora, chamaremos o primeiro serviço na cadeia de caracteres modificada.</span><span class="sxs-lookup"><span data-stu-id="8de78-161">We’ll now call the first service on the modified string.</span></span> <span data-ttu-id="8de78-162">Clique com o botão direito e selecione **adicionar referência de serviço**.</span><span class="sxs-lookup"><span data-stu-id="8de78-162">Right-click the project and select **Add Service Reference**.</span></span> <span data-ttu-id="8de78-163">Adicionar uma referência de serviço para o serviço em http://localhost/NestedServices/StringReverserService.xamlx e compilar o projeto para criar uma atividade personalizada para acessar o primeiro serviço Web.</span><span class="sxs-lookup"><span data-stu-id="8de78-163">Add a service reference to the service at http://localhost/NestedServices/StringReverserService.xamlx and build the project to create a custom activity to access the first Web service.</span></span>  
  
9. <span data-ttu-id="8de78-164">Arraste uma instância da nova atividade de fluxo de trabalho, entre o **InvokeMethod** atividade e o **SendReplyToReceive** atividades.</span><span class="sxs-lookup"><span data-stu-id="8de78-164">Drag an instance of the new activity onto the workflow, between the **InvokeMethod** activity and the **SendReplyToReceive** activities.</span></span> <span data-ttu-id="8de78-165">Atribua a variável StringToReverse à propriedade InputString da nova atividade e a variável StringToReturn à propriedade StringToReturn.</span><span class="sxs-lookup"><span data-stu-id="8de78-165">Assign the variable StringToReverse to the InputString property of the new activity, and the variable StringToReturn to the StringToReturn property.</span></span>  
  
10. <span data-ttu-id="8de78-166">Abra a página de propriedades para o projeto NestedServices e altere o **página específica** no **Web** tab para UpperCaserService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="8de78-166">Open the Properties page for the NestedServices project, and change the **Specific Page** in the **Web** tab to UpperCaserService.xamlx.</span></span>  
  
11. <span data-ttu-id="8de78-167">Teste o serviço pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="8de78-167">Test the service by pressing F5.</span></span> <span data-ttu-id="8de78-168">No cliente de teste de WCF é exibida, clique duas vezes o método ReverseString().</span><span class="sxs-lookup"><span data-stu-id="8de78-168">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="8de78-169">No painel de solicitação, digite `Sample` para o valor do parâmetro InputString.</span><span class="sxs-lookup"><span data-stu-id="8de78-169">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="8de78-170">Clique em **invocar**.</span><span class="sxs-lookup"><span data-stu-id="8de78-170">Click **Invoke**.</span></span> <span data-ttu-id="8de78-171">O serviço deve retornar "ELPMAS".</span><span class="sxs-lookup"><span data-stu-id="8de78-171">The service should return "ELPMAS".</span></span>  
  
### <a name="to-create-a-client-to-call-the-services"></a><span data-ttu-id="8de78-172">Para criar um cliente para chamar os serviços</span><span class="sxs-lookup"><span data-stu-id="8de78-172">To create a client to call the services</span></span>  
  
1.  <span data-ttu-id="8de78-173">Adicione um novo projeto de aplicativo de Console chamado cliente para a solução.</span><span class="sxs-lookup"><span data-stu-id="8de78-173">Add a new Console application project called Client to the solution.</span></span>  
  
2.  <span data-ttu-id="8de78-174">O projeto de cliente e selecione **adicionar referência de serviço**.</span><span class="sxs-lookup"><span data-stu-id="8de78-174">Right-click the Client project and select **Add Service Reference**.</span></span> <span data-ttu-id="8de78-175">Na janela que aparece, clique em **Discover**.</span><span class="sxs-lookup"><span data-stu-id="8de78-175">In the window that appears, click **Discover**.</span></span> <span data-ttu-id="8de78-176">Selecione StringReverserService.xamlx e, em seguida, digite ReverseService como o namespace.</span><span class="sxs-lookup"><span data-stu-id="8de78-176">Select StringReverserService.xamlx, and enter ReverseService as the namespace.</span></span>  <span data-ttu-id="8de78-177">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="8de78-177">Click **OK**.</span></span>  
  
3.  <span data-ttu-id="8de78-178">Substitua o método Main em Program.cs pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8de78-178">Replace the Main method in Program.cs with the following code.</span></span>  
  
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
