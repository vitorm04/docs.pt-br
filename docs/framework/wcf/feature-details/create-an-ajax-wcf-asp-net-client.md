---
title: Criar um serviço WCF habilitado para AJAX e um cliente ASP.NET no Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 1f5c9eb1750b0df28836f147d5b4be1b223bb52e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053688"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="00f98-102">Como: Criar um serviço WCF habilitado para AJAX e um cliente ASP.NET que acessa o serviço</span><span class="sxs-lookup"><span data-stu-id="00f98-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="00f98-103">Este tópico mostra como usar o Visual Studio para criar um serviço de Windows Communication Foundation habilitado para AJAX (WCF) e um cliente ASP.NET que acessa o serviço.</span><span class="sxs-lookup"><span data-stu-id="00f98-103">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="00f98-104">Criar um aplicativo Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="00f98-104">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="00f98-105">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="00f98-105">Open Visual Studio.</span></span>

1. <span data-ttu-id="00f98-106">No menu **arquivo** , selecione **novo** > **projeto**</span><span class="sxs-lookup"><span data-stu-id="00f98-106">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="00f98-107">Na caixa de diálogo **novo projeto** , expanda a categoria  > **Visual C#**  **Web** **instalada** > e selecione **ASP.NET aplicativo Web (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="00f98-107">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="00f98-108">Nomeie o projeto como **sanduícheservices** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="00f98-108">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="00f98-109">Na caixa de diálogo **novo aplicativo Web ASP.net** , selecione **vazio** e, em seguida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="00f98-109">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Caixa de diálogo tipo de aplicativo Web ASP.NET no Visual Studio](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="00f98-111">Adicionar um formulário da Web</span><span class="sxs-lookup"><span data-stu-id="00f98-111">Add a web form</span></span>

1. <span data-ttu-id="00f98-112">Clique com o botão direito do mouse no projeto sanduícheservices em **Gerenciador de soluções** e selecione **Adicionar** > **novo item**.</span><span class="sxs-lookup"><span data-stu-id="00f98-112">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="00f98-113">Na caixa de diálogo **Adicionar novo item** , expanda a  > categoria**Visual C#**  **Web** **instalada** > e selecione o modelo de **formulário da Web** .</span><span class="sxs-lookup"><span data-stu-id="00f98-113">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="00f98-114">Aceite o nome padrão (**WebForm1**) e, em seguida, selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="00f98-114">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="00f98-115">O *WebForm1. aspx* é aberto na exibição de **origem** .</span><span class="sxs-lookup"><span data-stu-id="00f98-115">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="00f98-116">Adicione a seguinte marcação dentro das marcas de  **\<> do corpo** :</span><span class="sxs-lookup"><span data-stu-id="00f98-116">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="00f98-117">Criar um serviço WCF habilitado para AJAX</span><span class="sxs-lookup"><span data-stu-id="00f98-117">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="00f98-118">Clique com o botão direito do mouse no projeto sanduícheservices em **Gerenciador de soluções** e selecione **Adicionar** > **novo item**.</span><span class="sxs-lookup"><span data-stu-id="00f98-118">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="00f98-119">Na caixa de diálogo **Adicionar novo item** ,  > expanda a categoria**Visual C#**  **Web** **instalada** > e selecione o modelo **serviço WCF (habilitado para Ajax)** .</span><span class="sxs-lookup"><span data-stu-id="00f98-119">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Modelo de item do serviço WCF (habilitado para AJAX) no Visual Studio](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="00f98-121">Nomeie o serviço **CostService** e, em seguida, selecione **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="00f98-121">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="00f98-122">*CostService.svc.cs* é aberto no editor.</span><span class="sxs-lookup"><span data-stu-id="00f98-122">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="00f98-123">Implemente a operação no serviço.</span><span class="sxs-lookup"><span data-stu-id="00f98-123">Implement the operation in the service.</span></span> <span data-ttu-id="00f98-124">Adicione o seguinte método à classe CostService para calcular o custo de uma quantidade de pizzas:</span><span class="sxs-lookup"><span data-stu-id="00f98-124">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="00f98-125">Configurar o cliente para acessar o serviço</span><span class="sxs-lookup"><span data-stu-id="00f98-125">Configure the client to access the service</span></span>

1. <span data-ttu-id="00f98-126">Abra o arquivo *WebForm1. aspx* e selecione o modo de exibição **design** .</span><span class="sxs-lookup"><span data-stu-id="00f98-126">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="00f98-127">No menu **Exibir** , selecione **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="00f98-127">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="00f98-128">Expanda o nó **extensões Ajax** e arraste e solte um **ScriptManager** no formulário.</span><span class="sxs-lookup"><span data-stu-id="00f98-128">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="00f98-129">De volta à exibição da **fonte** , adicione o seguinte código entre as marcas de  **\<> do ScriptManager** para especificar o caminho para o serviço WCF:</span><span class="sxs-lookup"><span data-stu-id="00f98-129">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. <span data-ttu-id="00f98-130">Adicione o código para a função `Calculate()`JavaScript.</span><span class="sxs-lookup"><span data-stu-id="00f98-130">Add the code for the Javascript function `Calculate()`.</span></span> <span data-ttu-id="00f98-131">Coloque o seguinte código na seção de **cabeçalho** do formulário da Web:</span><span class="sxs-lookup"><span data-stu-id="00f98-131">Place the following code in the **head** section of the web form:</span></span>

    ```html
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

   <span data-ttu-id="00f98-132">Esse código chama o método de CostService para calcular o preço de três pizzas e, em seguida, exibe o resultado na extensão chamada **additionResult**.</span><span class="sxs-lookup"><span data-stu-id="00f98-132">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="00f98-133">Execute o programa</span><span class="sxs-lookup"><span data-stu-id="00f98-133">Run the program</span></span>

<span data-ttu-id="00f98-134">Verifique se o *WebForm1. aspx* tem foco e pressione o botão **Iniciar** para iniciar o cliente Web.</span><span class="sxs-lookup"><span data-stu-id="00f98-134">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="00f98-135">O botão tem um triângulo verde e diz algo como **IIS Express (Microsoft Edge)** .</span><span class="sxs-lookup"><span data-stu-id="00f98-135">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="00f98-136">Ou, você pode pressionar **F5**.</span><span class="sxs-lookup"><span data-stu-id="00f98-136">Or, you can press **F5**.</span></span> <span data-ttu-id="00f98-137">Clique no botão **preço de 3 pizzas** para gerar a saída esperada de "3,75".</span><span class="sxs-lookup"><span data-stu-id="00f98-137">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example-code"></a><span data-ttu-id="00f98-138">Código de exemplo</span><span class="sxs-lookup"><span data-stu-id="00f98-138">Example code</span></span>

<span data-ttu-id="00f98-139">A seguir está o código completo no arquivo *CostService.svc.cs* :</span><span class="sxs-lookup"><span data-stu-id="00f98-139">Following is the full code in the *CostService.svc.cs* file :</span></span>

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

<span data-ttu-id="00f98-140">Veja a seguir o conteúdo completo da página *WebForm1. aspx* :</span><span class="sxs-lookup"><span data-stu-id="00f98-140">Following is the full contents of the *WebForm1.aspx* page:</span></span>

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
