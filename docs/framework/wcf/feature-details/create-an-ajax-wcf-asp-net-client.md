---
title: Criar um serviço WCF habilitado para AJAX e um cliente do ASP.NET no Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 954ee0409f370c3fa28814a70d51334fd75f7b79
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678276"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="c74b6-102">Como criar um serviço do WCF habilitado pelo AJAX em um cliente do ASP.NET que acessa o serviço</span><span class="sxs-lookup"><span data-stu-id="c74b6-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="c74b6-103">Este tópico mostra como usar o Visual Studio para criar um serviço habilitado para AJAX Windows Communication Foundation (WCF) e um cliente do ASP.NET que acessa o serviço.</span><span class="sxs-lookup"><span data-stu-id="c74b6-103">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="c74b6-104">Criar um aplicativo Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c74b6-104">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="c74b6-105">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c74b6-105">Open Visual Studio.</span></span>

1. <span data-ttu-id="c74b6-106">Dos **arquivo** menu, selecione **New** > **projeto**</span><span class="sxs-lookup"><span data-stu-id="c74b6-106">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="c74b6-107">No **novo projeto** caixa de diálogo, expanda o **instalado** > **Visual C#** > **Web** categoria e, em seguida, Selecione **aplicativo Web ASP.NET (.NET Framework)**.</span><span class="sxs-lookup"><span data-stu-id="c74b6-107">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="c74b6-108">Nomeie o projeto **SandwichServices** e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="c74b6-108">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="c74b6-109">No **novo aplicativo Web ASP.NET** caixa de diálogo, selecione **vazia** e, em seguida, selecione **Okey**.</span><span class="sxs-lookup"><span data-stu-id="c74b6-109">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Diálogo do tipo de aplicativo do ASP.NET web no Visual Studio](media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="c74b6-111">Adicionar um formulário da web</span><span class="sxs-lookup"><span data-stu-id="c74b6-111">Add a web form</span></span>

1. <span data-ttu-id="c74b6-112">Clique com botão direito no projeto SandwichServices no **Gerenciador de soluções** e selecione **Add** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="c74b6-112">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="c74b6-113">No **Adicionar Novo Item** caixa de diálogo, expanda o **instalado** > **Visual C#** > **Web** categoria e, em seguida, Selecione o **Web Form** modelo.</span><span class="sxs-lookup"><span data-stu-id="c74b6-113">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="c74b6-114">Aceite o nome padrão (**WebForm1**) e, em seguida, selecione **Add**.</span><span class="sxs-lookup"><span data-stu-id="c74b6-114">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="c74b6-115">*WebForm1.aspx* é aberto no **origem** modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="c74b6-115">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="c74b6-116">Adicione a seguinte marcação dentro de  **\<corpo >** marcas:</span><span class="sxs-lookup"><span data-stu-id="c74b6-116">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="c74b6-117">Criar um serviço WCF habilitado pelo AJAX</span><span class="sxs-lookup"><span data-stu-id="c74b6-117">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="c74b6-118">Clique com botão direito no projeto SandwichServices no **Gerenciador de soluções** e selecione **Add** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="c74b6-118">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="c74b6-119">No **Adicionar Novo Item** caixa de diálogo, expanda o **instalado** > **Visual C#** > **Web** categoria e, em seguida, Selecione o **serviço do WCF (habilitado para AJAX)** modelo.</span><span class="sxs-lookup"><span data-stu-id="c74b6-119">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Modelo de item (habilitado para AJAX) do serviço WCF no Visual Studio](media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="c74b6-121">Nomeie o serviço **CostService** e, em seguida, selecione **Add**.</span><span class="sxs-lookup"><span data-stu-id="c74b6-121">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="c74b6-122">*CostService.svc.cs* abre no editor.</span><span class="sxs-lookup"><span data-stu-id="c74b6-122">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="c74b6-123">Implemente a operação no serviço.</span><span class="sxs-lookup"><span data-stu-id="c74b6-123">Implement the operation in the service.</span></span> <span data-ttu-id="c74b6-124">Adicione o seguinte método à classe CostService para calcular o custo de uma quantidade de pizzas:</span><span class="sxs-lookup"><span data-stu-id="c74b6-124">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="c74b6-125">Configurar o cliente para acessar o serviço</span><span class="sxs-lookup"><span data-stu-id="c74b6-125">Configure the client to access the service</span></span>

1. <span data-ttu-id="c74b6-126">Abra o *WebForm1.aspx* do arquivo e selecione o **Design** modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="c74b6-126">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="c74b6-127">Dos **modo de exibição** menu, selecione **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="c74b6-127">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="c74b6-128">Expanda o **extensões AJAX** nó e arraste e solte um **ScriptManager** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="c74b6-128">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="c74b6-129">Volta a **fonte** exiba, adicione o seguinte código entre o  **\<ScriptManager >** marcas para especificar o caminho para o serviço WCF:</span><span class="sxs-lookup"><span data-stu-id="c74b6-129">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```html
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

1. <span data-ttu-id="c74b6-130">Adicione o código para a função Javascript `Calculate()`.</span><span class="sxs-lookup"><span data-stu-id="c74b6-130">Add the code for the Javascript function `Calculate()`.</span></span> <span data-ttu-id="c74b6-131">Coloque o seguinte código na **head** seção do formulário da web:</span><span class="sxs-lookup"><span data-stu-id="c74b6-131">Place the following code in the **head** section of the web form:</span></span>

    ```javascript
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
    ```

   <span data-ttu-id="c74b6-132">Esse código chama o método de CostService para calcular o preço para três pizzas e, em seguida, exibe o resultado no período chamado **additionResult**.</span><span class="sxs-lookup"><span data-stu-id="c74b6-132">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="c74b6-133">Execute o programa</span><span class="sxs-lookup"><span data-stu-id="c74b6-133">Run the program</span></span>

<span data-ttu-id="c74b6-134">Certifique-se de que *WebForm1.aspx* tem o foco e pressione **iniciar** botão para iniciar o cliente web.</span><span class="sxs-lookup"><span data-stu-id="c74b6-134">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="c74b6-135">O botão tem um triângulo verde e diz algo como **IIS Express (Microsoft Edge)**.</span><span class="sxs-lookup"><span data-stu-id="c74b6-135">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="c74b6-136">Ou, você pode pressionar **F5**.</span><span class="sxs-lookup"><span data-stu-id="c74b6-136">Or, you can press **F5**.</span></span> <span data-ttu-id="c74b6-137">Clique o **preço de 3 pizzas** botão para gerar a saída esperada do "3,75".</span><span class="sxs-lookup"><span data-stu-id="c74b6-137">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example-code"></a><span data-ttu-id="c74b6-138">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="c74b6-138">Example code</span></span>

<span data-ttu-id="c74b6-139">A seguir está o código completo na *CostService.svc.cs* arquivo:</span><span class="sxs-lookup"><span data-stu-id="c74b6-139">Following is the full code in the *CostService.svc.cs* file :</span></span>

```csharp
using System.ServiceModel;
using System.ServiceModel.Activation;

namespace SandwichServices
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class CostService
    {
        [OperationContract]
        public double CostOfSandwiches(int quantity)
        {
            return 1.25 * quantity;
        }
    }
}
```

<span data-ttu-id="c74b6-140">A seguir está o conteúdo completo do *WebForm1.aspx* página:</span><span class="sxs-lookup"><span data-stu-id="c74b6-140">Following is the full contents of the *WebForm1.aspx* page:</span></span>

```aspx-csharp
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SandwichServices.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <asp:ScriptManager ID="ScriptManager1" runat="server">
            <Services>
                <asp:ServiceReference Path="~/CostService.svc" />
            </Services>
        </asp:ScriptManager>

        <input type="button" value="Price of 3 sandwiches" onclick="Calculate()" />
        <br />
        <span id="additionResult"></span>
    </form>
</body>
</html>
```
