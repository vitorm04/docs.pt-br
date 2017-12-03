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
ms.openlocfilehash: b136565730c1b3175abff8b057a69acc6609a44d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Como criar um serviço do WCF habilitado pelo AJAX em um cliente do ASP.NET que acessa o serviço
Este tópico mostra como usar o Visual Studio 2008 para criar um habilitado pelo AJAX [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço e um cliente do ASP.NET que acessa o serviço. O código para o serviço e para o cliente são fornecidos na seção de exemplo, após as etapas para criá-los são descritas na seção de procedimentos.  
  
### <a name="to-create-the-aspnet-client-application"></a>Para criar o aplicativo de cliente do ASP.NET  
  
1.  Abra [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Do **arquivo** menu, selecione **novo**, em seguida, **projeto**, em seguida, **Web**e, em seguida, selecione **doaplicativodeWebdoASP.NET**.  
  
3.  Nomeie o projeto `SandwichServices` e clique em **Okey**.  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a>Para criar o serviço WCF AJAX habilitado  
  
1.  Com o botão direito do `SandwichServices` project no **Gerenciador de soluções** janela e selecione **adicionar**, em seguida, **Novo Item**e, em seguida, **serviço do WCF habilitado para AJAX** .  
  
2.  O serviço de nomes `CostService` no **nome** caixa e clique em **adicionar**.  
  
3.  Abra o arquivo CostService.svc.cs.  
  
4.  Especifique o `Namespace` para <xref:System.ServiceModel.ServiceContractAttribute> como `SandwichService`:  
  
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
  
5.  Implemente as operações no serviço. Adicionar o <xref:System.ServiceModel.OperationContractAttribute> para cada uma das operações para indicar que fazem parte do contrato. O exemplo a seguir implementa um método que retorna o custo de uma determinada quantidade de pizzas.  
  
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
  
### <a name="to-configure-the-client-to-access-the-service"></a>Para configurar o cliente para acessar o serviço  
  
1.  Abra a página Default.aspx e selecione o **Design** exibição.  
  
2.  Do **exibição** menu, selecione **caixa de ferramentas**.  
  
3.  Expanda o **extensões AJAX** nó e arrastar e soltar uma **ScriptManager** na página Default.aspx.  
  
4.  Clique com botão direito do **ScriptManager** e selecione **propriedades**.  
  
5.  Expanda o **serviços** coleção no **propriedades** janela para abrir o **Editor de coleção ServiceReference** janela.  
  
6.  Clique em **adicionar**, especifique `CostService.svc` como o **caminho** referenciados e, em seguida, clique em **Okey**.  
  
7.  Expanda o **HTML** nó o **caixa de ferramentas** e arraste e solte um **entrada (botão)** na página Default.aspx.  
  
8.  Clique com botão direito do **botão** e selecione **propriedades**.  
  
9. Alterar o **valor** campo `Price for 3 Sandwiches`.  
  
10. Clique duas vezes o **botão** para acessar o código JavaScript.  
  
11. Passe o seguinte código JavaScript dentro de <`script`> elemento.  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a>Para acessar o serviço do cliente  
  
1.  Use Ctrl + F5 para iniciar o serviço e o cliente da Web. Clique o **preço para 3 pizzas grelhado** botão para gerar a saída esperada do "3,75".  
  
## <a name="example"></a>Exemplo  
 Este exemplo contém o código de serviço contido no arquivo WCFService.svc.cs e o código do cliente contidos no arquivo default. aspx.  
  
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
