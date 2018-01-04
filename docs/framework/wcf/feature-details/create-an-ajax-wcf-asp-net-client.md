---
title: "Como criar um serviço do WCF habilitado pelo AJAX em um cliente do ASP.NET que acessa o serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aafa15129e4a131c5f50eb3296a87fc141e1bda6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="036a4-102">Como criar um serviço do WCF habilitado pelo AJAX em um cliente do ASP.NET que acessa o serviço</span><span class="sxs-lookup"><span data-stu-id="036a4-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>
<span data-ttu-id="036a4-103">Este tópico mostra como usar o Visual Studio 2008 para criar um habilitado pelo AJAX [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço e um cliente do ASP.NET que acessa o serviço.</span><span class="sxs-lookup"><span data-stu-id="036a4-103">This topic shows how to use Visual Studio 2008 to create an AJAX-enabled [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and an ASP.NET client that accesses the service.</span></span> <span data-ttu-id="036a4-104">O código para o serviço e para o cliente são fornecidos na seção de exemplo, após as etapas para criá-los são descritas na seção de procedimentos.</span><span class="sxs-lookup"><span data-stu-id="036a4-104">The code for the service and for the client are provided in the Example section after the steps for creating them are described in the Procedures section.</span></span>  
  
### <a name="to-create-the-aspnet-client-application"></a><span data-ttu-id="036a4-105">Para criar o aplicativo de cliente do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="036a4-105">To create the ASP.NET client application</span></span>  
  
1.  <span data-ttu-id="036a4-106">Abra [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="036a4-106">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="036a4-107">Do **arquivo** menu, selecione **novo**, em seguida, **projeto**, em seguida, **Web**e, em seguida, selecione **doaplicativodeWebdoASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="036a4-107">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Application**.</span></span>  
  
3.  <span data-ttu-id="036a4-108">Nomeie o projeto `SandwichServices` e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="036a4-108">Name the Project `SandwichServices` and click **OK**.</span></span>  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a><span data-ttu-id="036a4-109">Para criar o serviço WCF AJAX habilitado</span><span class="sxs-lookup"><span data-stu-id="036a4-109">To create the WCF AJAX-enabled service</span></span>  
  
1.  <span data-ttu-id="036a4-110">Com o botão direito do `SandwichServices` project no **Gerenciador de soluções** janela e selecione **adicionar**, em seguida, **Novo Item**e, em seguida, **serviço do WCF habilitado para AJAX** .</span><span class="sxs-lookup"><span data-stu-id="036a4-110">Right-click the `SandwichServices` project in the **Solution Explorer** window and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>  
  
2.  <span data-ttu-id="036a4-111">O serviço de nomes `CostService` no **nome** caixa e clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="036a4-111">Name the service `CostService` in the **Name** box and click **Add**.</span></span>  
  
3.  <span data-ttu-id="036a4-112">Abra o arquivo CostService.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="036a4-112">Open the CostService.svc.cs file.</span></span>  
  
4.  <span data-ttu-id="036a4-113">Especifique o `Namespace` para <xref:System.ServiceModel.ServiceContractAttribute> como `SandwichService`:</span><span class="sxs-lookup"><span data-stu-id="036a4-113">Specify the `Namespace` for <xref:System.ServiceModel.ServiceContractAttribute> as `SandwichService`:</span></span>  
  
    ```  
    namespace SandwichServices  
    {  
      [ServiceContract(Namespace = "SandwichServices")]  
      [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
       public class CostService  
       {  
         …  
       }  
     }  
    ```  
  
5.  <span data-ttu-id="036a4-114">Implemente as operações no serviço.</span><span class="sxs-lookup"><span data-stu-id="036a4-114">Implement the operations in the service.</span></span> <span data-ttu-id="036a4-115">Adicionar o <xref:System.ServiceModel.OperationContractAttribute> para cada uma das operações para indicar que fazem parte do contrato.</span><span class="sxs-lookup"><span data-stu-id="036a4-115">Add the <xref:System.ServiceModel.OperationContractAttribute> to each of the operations to indicate that they are part of the contract.</span></span> <span data-ttu-id="036a4-116">O exemplo a seguir implementa um método que retorna o custo de uma determinada quantidade de pizzas.</span><span class="sxs-lookup"><span data-stu-id="036a4-116">The following example implements a method that returns the cost of a given quantity of sandwiches.</span></span>  
  
    ```  
    public class CostService  
    {  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
    // Add more operations here and mark them with [OperationContract]  
    }  
    ```  
  
### <a name="to-configure-the-client-to-access-the-service"></a><span data-ttu-id="036a4-117">Para configurar o cliente para acessar o serviço</span><span class="sxs-lookup"><span data-stu-id="036a4-117">To configure the client to access the service</span></span>  
  
1.  <span data-ttu-id="036a4-118">Abra a página Default.aspx e selecione o **Design** exibição.</span><span class="sxs-lookup"><span data-stu-id="036a4-118">Open the Default.aspx page and select the **Design** view.</span></span>  
  
2.  <span data-ttu-id="036a4-119">Do **exibição** menu, selecione **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="036a4-119">From the **View** menu, select **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="036a4-120">Expanda o **extensões AJAX** nó e arrastar e soltar uma **ScriptManager** na página Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="036a4-120">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** on to the Default.aspx page.</span></span>  
  
4.  <span data-ttu-id="036a4-121">Clique com botão direito do **ScriptManager** e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="036a4-121">Right-click the **ScriptManager** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="036a4-122">Expanda o **serviços** coleção no **propriedades** janela para abrir o **Editor de coleção ServiceReference** janela.</span><span class="sxs-lookup"><span data-stu-id="036a4-122">Expand the **Services** collection in the **Properties** window to open up the **ServiceReference Collection Editor** window.</span></span>  
  
6.  <span data-ttu-id="036a4-123">Clique em **adicionar**, especifique `CostService.svc` como o **caminho** referenciados e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="036a4-123">Click **Add**, specify `CostService.svc` as the **Path** referenced, and click **OK**.</span></span>  
  
7.  <span data-ttu-id="036a4-124">Expanda o **HTML** nó o **caixa de ferramentas** e arraste e solte um **entrada (botão)** na página Default.aspx.</span><span class="sxs-lookup"><span data-stu-id="036a4-124">Expand the **HTML** node in the **Toolbox** and drag and drop an **Input (Button)** on to the Default.aspx page.</span></span>  
  
8.  <span data-ttu-id="036a4-125">Clique com botão direito do **botão** e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="036a4-125">Right-click the **Button** and select **Properties**.</span></span>  
  
9. <span data-ttu-id="036a4-126">Alterar o **valor** campo `Price for 3 Sandwiches`.</span><span class="sxs-lookup"><span data-stu-id="036a4-126">Change the **Value** field to `Price for 3 Sandwiches`.</span></span>  
  
10. <span data-ttu-id="036a4-127">Clique duas vezes o **botão** para acessar o código JavaScript.</span><span class="sxs-lookup"><span data-stu-id="036a4-127">Double-click the **Button** to access the JavaScript code.</span></span>  
  
11. <span data-ttu-id="036a4-128">Passe o seguinte código JavaScript dentro de <`script`> elemento.</span><span class="sxs-lookup"><span data-stu-id="036a4-128">Pass in the following JavaScript code within the <`script`> element.</span></span>  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a><span data-ttu-id="036a4-129">Para acessar o serviço do cliente</span><span class="sxs-lookup"><span data-stu-id="036a4-129">To access the service from the client</span></span>  
  
1.  <span data-ttu-id="036a4-130">Use Ctrl + F5 para iniciar o serviço e o cliente da Web.</span><span class="sxs-lookup"><span data-stu-id="036a4-130">Use Ctrl +F5 to launch the service and the Web client.</span></span> <span data-ttu-id="036a4-131">Clique o **preço para 3 pizzas grelhado** botão para gerar a saída esperada do "3,75".</span><span class="sxs-lookup"><span data-stu-id="036a4-131">Click the **Price for 3 Grilled Sandwiches** button to generate the expected output of "3.75".</span></span>  
  
## <a name="example"></a><span data-ttu-id="036a4-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="036a4-132">Example</span></span>  
 <span data-ttu-id="036a4-133">Este exemplo contém o código de serviço contido no arquivo WCFService.svc.cs e o código do cliente contidos no arquivo default. aspx.</span><span class="sxs-lookup"><span data-stu-id="036a4-133">This example contains the service code contained in the WCFService.svc.cs file and the client code contained in the Default.aspx file.</span></span>  
  
```  
//The service code contained in the CostService.svc.cs file.  
  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace SandwichServices  
{  
    [ServiceContract(Namespace="SandwichServices")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class CostService  
    {  
        // Add [WebGet] attribute to use HTTP GET  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
        // Add more operations here and mark them with [OperationContract]  
    }  
}  
//The code for hosting the service is contained in the CostService.svc file.  
  
<%@ ServiceHost Language="C#" Debug="true" Service="SandwichServices.CostService" CodeBehind="CostService.svc.cs" %>  
  
//The client code contained in the Default.aspx file.  
  
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="SandwichServices._Default" %>  
  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
  
<html >  
<head runat="server">  
    <title>Untitled Page</title>  
<script language="javascript" type="text/javascript">  
// <!CDATA[  
  
function Button1_onclick() {  
var service = new SandwichServices.CostService();  
service.CostOfSandwiches(3, onSuccess, null, null);  
}  
  
function onSuccess(result){  
alert(result);  
}  
  
// ]]>  
</script>  
</head>  
<body>  
    <form id="form1" runat="server">  
    <div>  
  
    </div>  
    <asp:ScriptManager ID="ScriptManager1" runat="server">  
        <services>  
            <asp:servicereference Path="CostService.svc" />  
        </services>  
    </asp:ScriptManager>  
    </form>  
    <p>  
        <input id="Button1" type="button" value="Price for 3 Sandwiches" onclick="return Button1_onclick()" /></p>  
</body>  
</html>  
```     
