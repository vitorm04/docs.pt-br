---
title: Como criar um serviço de fluxo de trabalho que chama outro serviço de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: 1b30da34f7c85cccd98b18cd32b81c83630989b2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216126"
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a><span data-ttu-id="5866a-102">Como criar um serviço de fluxo de trabalho que chama outro serviço de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="5866a-102">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>

<span data-ttu-id="5866a-103">Às vezes, é necessário para um serviço de fluxo de trabalho obter informações de outro serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5866a-103">It is sometimes necessary for a workflow service to obtain information from another workflow service.</span></span> <span data-ttu-id="5866a-104">Este tópico demonstra como chamar um serviço de fluxo de trabalho de outro.</span><span class="sxs-lookup"><span data-stu-id="5866a-104">This topic demonstrates how to call one workflow service from another.</span></span> <span data-ttu-id="5866a-105">Neste tópico, vamos criar dois serviços de fluxo de trabalho; um que tem um método que reverte a cadeia de caracteres de entrada e outra que converte a cadeia de caracteres de entrada em maiuscula depois de reverter a cadeia de caracteres que usa o serviço primeiro.</span><span class="sxs-lookup"><span data-stu-id="5866a-105">In this topic, we’ll create two workflow services; one that has a method that reverses the input string, and another that converts the input string to uppercase after reversing the string that uses the first service.</span></span>

### <a name="to-create-the-reverser-workflow-service"></a><span data-ttu-id="5866a-106">Para criar o serviço de fluxo de trabalho reversor</span><span class="sxs-lookup"><span data-stu-id="5866a-106">To create the Reverser workflow service</span></span>

1.  <span data-ttu-id="5866a-107">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5866a-107">Open Visual Studio.</span></span>

2.  <span data-ttu-id="5866a-108">Selecione **arquivo** > **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="5866a-108">Select **File** > **New Project**.</span></span> <span data-ttu-id="5866a-109">Sob o **fluxo de trabalho** nó na **modelos instalados** painel, selecione **aplicativo de serviço de fluxo de trabalho WCF**.</span><span class="sxs-lookup"><span data-stu-id="5866a-109">Under the **Workflow** node in the **Installed Templates** pane, select **WCF Workflow Service Application**.</span></span> <span data-ttu-id="5866a-110">Nomeie a solução `NestedServices` e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="5866a-110">Name the solution `NestedServices` and then click **OK**.</span></span>

3.  <span data-ttu-id="5866a-111">Sob **servidores**, verifique se **usar servidor Web do IIS Local** é selecionado.</span><span class="sxs-lookup"><span data-stu-id="5866a-111">Under **Servers**, make sure that **Use Local IIS Web Server** is selected.</span></span> <span data-ttu-id="5866a-112">Clique em **criar diretório Virtual**.</span><span class="sxs-lookup"><span data-stu-id="5866a-112">Click **Create Virtual Directory**.</span></span> <span data-ttu-id="5866a-113">Clique em **Okey** na caixa de diálogo informando que o diretório virtual foi criado com êxito.</span><span class="sxs-lookup"><span data-stu-id="5866a-113">Click **OK** in the dialog box stating that the virtual directory was successfully created.</span></span>

4.  <span data-ttu-id="5866a-114">No Gerenciador de soluções, renomeie Service1.xamlx para `StringReverserService.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="5866a-114">In Solution Explorer, rename Service1.xamlx to `StringReverserService.xamlx`.</span></span>

5.  <span data-ttu-id="5866a-115">Sobre o **propriedades do projeto** para o novo projeto, clique no **Web** guia. Defina as **iniciar ação** para **página específica**e selecione StringReverserService.xamlx como a página para iniciar.</span><span class="sxs-lookup"><span data-stu-id="5866a-115">On the **Project Properties** page for the new project, click the **Web** tab. Set the **Start Action** to **Specific Page**, and select StringReverserService.xamlx as the page to start.</span></span>

6.  <span data-ttu-id="5866a-116">Abra StringReverserService.xamlx no designer e exclua o existente `ReceiveRequest` e `SendReply` atividades e, em seguida, arraste um `ReceiveAndSendReply` atividade na atividade de sequência existente.</span><span class="sxs-lookup"><span data-stu-id="5866a-116">Open StringReverserService.xamlx in the designer and delete the existing `ReceiveRequest` and `SendReply` activities, and then drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>

    1.  <span data-ttu-id="5866a-117">Defina as **OperationName** para ReverseString.</span><span class="sxs-lookup"><span data-stu-id="5866a-117">Set the **OperationName** to ReverseString.</span></span>

    2.  <span data-ttu-id="5866a-118">Defina as **ServiceContractName** para IReverseString.</span><span class="sxs-lookup"><span data-stu-id="5866a-118">Set the **ServiceContractName** to IReverseString.</span></span>

    3.  <span data-ttu-id="5866a-119">Selecione o **CanCreateInstance** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="5866a-119">Select the **CanCreateInstance** check box.</span></span>

7.  <span data-ttu-id="5866a-120">Selecione o **SequentialService** atividade e, em seguida, clique o **variáveis** guia na parte inferior do designer.</span><span class="sxs-lookup"><span data-stu-id="5866a-120">Select the **SequentialService** activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="5866a-121">Crie duas novas variáveis nomeadas StringToReverse e ReversedStringToReturn do tipo cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5866a-121">Create two new variables named StringToReverse and ReversedStringToReturn of type String.</span></span>

8.  <span data-ttu-id="5866a-122">Clique o **definir** link na **Receive** atividade.</span><span class="sxs-lookup"><span data-stu-id="5866a-122">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="5866a-123">Clique o **parâmetros**e crie um parâmetro denominado InputString do tipo cadeia de caracteres que atribui a StringToReverse.</span><span class="sxs-lookup"><span data-stu-id="5866a-123">Click the  **Parameters**, and create a parameter named InputString of type String that assigns to StringToReverse.</span></span>

9. <span data-ttu-id="5866a-124">Clique o **definir** link na **SendReplyToReceive** atividade.</span><span class="sxs-lookup"><span data-stu-id="5866a-124">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="5866a-125">Clique o **parâmetros**e crie um parâmetro denominado ReversedString do tipo cadeia de caracteres atribuído a ReversedStringToReturn.</span><span class="sxs-lookup"><span data-stu-id="5866a-125">Click the **Parameters**, and create a parameter named ReversedString of type String, assigned to ReversedStringToReturn.</span></span>

10. <span data-ttu-id="5866a-126">Para implementar a lógica para o serviço, crie uma nova classe no projeto chamado StringLibrary.</span><span class="sxs-lookup"><span data-stu-id="5866a-126">To implement the logic for the service, create a new class in the project called StringLibrary.</span></span>  <span data-ttu-id="5866a-127">Substitua a definição de classe com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5866a-127">Replace the class definition with the following code.</span></span>

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

11. <span data-ttu-id="5866a-128">Para chamar o método ReverseString na entrada, arraste uma **InvokeMethod** atividade da caixa de ferramentas para o espaço entre o **Receive** e **SendReply** atividades.</span><span class="sxs-lookup"><span data-stu-id="5866a-128">To call the ReverseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="5866a-129">Defina as propriedades da atividade da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5866a-129">Set the properties of the activity as follows:</span></span>

    1.  <span data-ttu-id="5866a-130">**MethodName**: ReverseString</span><span class="sxs-lookup"><span data-stu-id="5866a-130">**MethodName**: ReverseString</span></span>

    2.  <span data-ttu-id="5866a-131">**Resultado**: ReversedStringToReturn</span><span class="sxs-lookup"><span data-stu-id="5866a-131">**Result**: ReversedStringToReturn</span></span>

    3.  <span data-ttu-id="5866a-132">**Parâmetros**: criar um novo parâmetro com um **direção** no, um **tipo** da cadeia de caracteres e uma **valor** de StringToReverse.</span><span class="sxs-lookup"><span data-stu-id="5866a-132">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToReverse.</span></span>

    4.  <span data-ttu-id="5866a-133">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="5866a-133">**TargetType**: NestedServices.StringLibrary</span></span>

12. <span data-ttu-id="5866a-134">Teste o serviço pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="5866a-134">Test the service by pressing F5.</span></span> <span data-ttu-id="5866a-135">No cliente de teste de WCF é exibida, clique duas vezes o método ReverseString().</span><span class="sxs-lookup"><span data-stu-id="5866a-135">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="5866a-136">No painel de solicitação, insira `Sample` para o valor do parâmetro InputString.</span><span class="sxs-lookup"><span data-stu-id="5866a-136">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="5866a-137">Clique em **invocar**.</span><span class="sxs-lookup"><span data-stu-id="5866a-137">Click **Invoke**.</span></span> <span data-ttu-id="5866a-138">O serviço deve retornar "elpmaS".</span><span class="sxs-lookup"><span data-stu-id="5866a-138">The service should return "elpmaS".</span></span>

### <a name="to-create-the-uppercaser-workflow-service"></a><span data-ttu-id="5866a-139">Para criar o serviço de fluxo de trabalho UpperCaser</span><span class="sxs-lookup"><span data-stu-id="5866a-139">To create the UpperCaser workflow service</span></span>

1.  <span data-ttu-id="5866a-140">Clique com botão direito no projeto NestedServices e selecione **Add** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="5866a-140">Right-click the NestedServices project and select **Add** > **New Item**.</span></span> <span data-ttu-id="5866a-141">No **fluxo de trabalho** nó, selecione **serviço de fluxo de trabalho WCF**e nomeie o novo serviço `UpperCaserService`.</span><span class="sxs-lookup"><span data-stu-id="5866a-141">In the **Workflow** node, select **WCF Workflow Service**, and name the new service `UpperCaserService`.</span></span> <span data-ttu-id="5866a-142">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="5866a-142">Click **Add**.</span></span> <span data-ttu-id="5866a-143">Isso deve adicionar um novo serviço de fluxo de trabalho chamado UpperCaserService.xamlx ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5866a-143">This should add a new workflow service called UpperCaserService.xamlx to the project.</span></span>

2.  <span data-ttu-id="5866a-144">Abra UpperCaserService.xamlx no designer e exclua o existente **ReceiveRequest** e `SendReply` atividades e arraste um `ReceiveAndSendReply` atividade na atividade de sequência existente.</span><span class="sxs-lookup"><span data-stu-id="5866a-144">Open UpperCaserService.xamlx in the designer and delete the existing **ReceiveRequest** and `SendReply` activities, and drag a `ReceiveAndSendReply` activity into the existing sequence activity.</span></span>

    1.  <span data-ttu-id="5866a-145">Defina as **OperationName** para UpperCaseString.</span><span class="sxs-lookup"><span data-stu-id="5866a-145">Set the **OperationName** to UpperCaseString.</span></span>

    2.  <span data-ttu-id="5866a-146">Defina as **ServiceContractName** para IUpperCaseString.</span><span class="sxs-lookup"><span data-stu-id="5866a-146">Set the **ServiceContractName** to IUpperCaseString.</span></span>

    3.  <span data-ttu-id="5866a-147">Selecione o **CanCreateInstance** caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="5866a-147">Select the **CanCreateInstance** check box.</span></span>

3.  <span data-ttu-id="5866a-148">Selecione a atividade de SequentialService e, em seguida, clique no **variáveis** guia na parte inferior do designer.</span><span class="sxs-lookup"><span data-stu-id="5866a-148">Select the SequentialService activity, and then click the **Variables** tab at the bottom of the designer.</span></span> <span data-ttu-id="5866a-149">Crie três novas variáveis nomeadas StringToUpper, StringToReverse e StringToReturn do tipo cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5866a-149">Create three new variables named StringToUpper, StringToReverse, and StringToReturn of type String.</span></span>

4.  <span data-ttu-id="5866a-150">Clique o **definir** link na **Receive** atividade.</span><span class="sxs-lookup"><span data-stu-id="5866a-150">Click the **Define** link in the **Receive** activity.</span></span> <span data-ttu-id="5866a-151">Clique o **parâmetros**e crie um parâmetro denominado InputString do tipo cadeia de caracteres que atribui a StringToUpper.</span><span class="sxs-lookup"><span data-stu-id="5866a-151">Click the **Parameters**, and create a parameter named InputString of type String that assigns to StringToUpper.</span></span>

5.  <span data-ttu-id="5866a-152">Clique o **definir** link na **SendReplyToReceive** atividade.</span><span class="sxs-lookup"><span data-stu-id="5866a-152">Click the **Define** link in the **SendReplyToReceive** activity.</span></span> <span data-ttu-id="5866a-153">Clique o **parâmetros**e crie um parâmetro denominado ModifiedString do tipo cadeia de caracteres atribuído a StringToReturn.</span><span class="sxs-lookup"><span data-stu-id="5866a-153">Click the **Parameters**, and create a parameter named ModifiedString of type String, assigned to StringToReturn.</span></span>

6.  <span data-ttu-id="5866a-154">Para implementar a lógica para o serviço, crie um novo método na classe StringLibrary usando o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5866a-154">To implement the logic for the service, create a new method in the StringLibrary class using the following code.</span></span>

    ```
    public static String UpperCaseString(string StringToUpperCase)
    {
         return StringToUpperCase.ToUpper();

    }
    ```

7.  <span data-ttu-id="5866a-155">Para chamar o método UpperCaseString na entrada, arraste uma **InvokeMethod** atividade da caixa de ferramentas para o espaço entre o **Receive** e **SendReply** atividades.</span><span class="sxs-lookup"><span data-stu-id="5866a-155">To call the UpperCaseString method on the input, drag an **InvokeMethod** activity from the toolbox to the space between the **Receive** and **SendReply** activities.</span></span> <span data-ttu-id="5866a-156">Defina as propriedades da atividade da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5866a-156">Set the properties of the activity as follows:</span></span>

    1.  <span data-ttu-id="5866a-157">**MethodName**: UpperCaseString</span><span class="sxs-lookup"><span data-stu-id="5866a-157">**MethodName**: UpperCaseString</span></span>

    2.  <span data-ttu-id="5866a-158">**Resultado**: StringToReverse</span><span class="sxs-lookup"><span data-stu-id="5866a-158">**Result**: StringToReverse</span></span>

    3.  <span data-ttu-id="5866a-159">**Parâmetros**: criar um novo parâmetro com um **direção** no, um **tipo** da cadeia de caracteres e uma **valor** de StringToUpper.</span><span class="sxs-lookup"><span data-stu-id="5866a-159">**Parameters**: Create a new parameter with a **Direction** of In, a **Type** of String, and a **Value** of StringToUpper.</span></span>

    4.  <span data-ttu-id="5866a-160">**TargetType**: NestedServices.StringLibrary</span><span class="sxs-lookup"><span data-stu-id="5866a-160">**TargetType**: NestedServices.StringLibrary</span></span>

8.  <span data-ttu-id="5866a-161">Agora, chamaremos o primeiro serviço na cadeia de caracteres modificada.</span><span class="sxs-lookup"><span data-stu-id="5866a-161">We’ll now call the first service on the modified string.</span></span> <span data-ttu-id="5866a-162">Clique com botão direito no projeto e selecione **Add** > **referência de serviço**.</span><span class="sxs-lookup"><span data-stu-id="5866a-162">Right-click the project and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="5866a-163">Adicionar uma referência de serviço para o serviço em http://localhost/NestedServices/StringReverserService.xamlx e compile o projeto para criar uma atividade personalizada para acessar o primeiro serviço Web.</span><span class="sxs-lookup"><span data-stu-id="5866a-163">Add a service reference to the service at http://localhost/NestedServices/StringReverserService.xamlx and build the project to create a custom activity to access the first Web service.</span></span>

9. <span data-ttu-id="5866a-164">Arraste uma instância da nova atividade para o fluxo de trabalho entre o **InvokeMethod** atividade e o **SendReplyToReceive** atividades.</span><span class="sxs-lookup"><span data-stu-id="5866a-164">Drag an instance of the new activity onto the workflow, between the **InvokeMethod** activity and the **SendReplyToReceive** activities.</span></span> <span data-ttu-id="5866a-165">Atribua a variável StringToReverse à propriedade InputString da nova atividade e a variável StringToReturn à propriedade StringToReturn.</span><span class="sxs-lookup"><span data-stu-id="5866a-165">Assign the variable StringToReverse to the InputString property of the new activity, and the variable StringToReturn to the StringToReturn property.</span></span>

10. <span data-ttu-id="5866a-166">Abra a página de propriedades para o projeto NestedServices e altere o **página específica** na **Web** tab para UpperCaserService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="5866a-166">Open the Properties page for the NestedServices project, and change the **Specific Page** in the **Web** tab to UpperCaserService.xamlx.</span></span>

11. <span data-ttu-id="5866a-167">Teste o serviço pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="5866a-167">Test the service by pressing F5.</span></span> <span data-ttu-id="5866a-168">No cliente de teste de WCF é exibida, clique duas vezes o método ReverseString().</span><span class="sxs-lookup"><span data-stu-id="5866a-168">In the WCF Test Client that appears, double-click the ReverseString() method.</span></span> <span data-ttu-id="5866a-169">No painel de solicitação, insira `Sample` para o valor do parâmetro InputString.</span><span class="sxs-lookup"><span data-stu-id="5866a-169">In the Request pane, enter `Sample` for the Value of the InputString parameter.</span></span> <span data-ttu-id="5866a-170">Clique em **invocar**.</span><span class="sxs-lookup"><span data-stu-id="5866a-170">Click **Invoke**.</span></span> <span data-ttu-id="5866a-171">O serviço deve retornar "ELPMAS".</span><span class="sxs-lookup"><span data-stu-id="5866a-171">The service should return "ELPMAS".</span></span>

### <a name="to-create-a-client-to-call-the-services"></a><span data-ttu-id="5866a-172">Para criar um cliente para chamar os serviços</span><span class="sxs-lookup"><span data-stu-id="5866a-172">To create a client to call the services</span></span>

1.  <span data-ttu-id="5866a-173">Adicione um novo projeto de aplicativo de Console chamado cliente à solução.</span><span class="sxs-lookup"><span data-stu-id="5866a-173">Add a new Console application project called Client to the solution.</span></span>

2.  <span data-ttu-id="5866a-174">O projeto de cliente com o botão direito e selecione **Add** > **referência de serviço**.</span><span class="sxs-lookup"><span data-stu-id="5866a-174">Right-click the Client project and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="5866a-175">Na janela que aparece, clique em **Discover**.</span><span class="sxs-lookup"><span data-stu-id="5866a-175">In the window that appears, click **Discover**.</span></span> <span data-ttu-id="5866a-176">Selecione StringReverserService.xamlx e insira ReverseService como o namespace.</span><span class="sxs-lookup"><span data-stu-id="5866a-176">Select StringReverserService.xamlx, and enter ReverseService as the namespace.</span></span>  <span data-ttu-id="5866a-177">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5866a-177">Click **OK**.</span></span>

3.  <span data-ttu-id="5866a-178">Substitua o método Main em Program.cs pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5866a-178">Replace the Main method in Program.cs with the following code.</span></span>

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