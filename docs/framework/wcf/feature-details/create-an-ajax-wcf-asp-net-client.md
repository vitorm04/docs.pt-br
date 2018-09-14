---
title: Criar um serviço WCF habilitado para AJAX e um cliente do ASP.NET no Visual Studio
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 954ee0409f370c3fa28814a70d51334fd75f7b79
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558035"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Como criar um serviço do WCF habilitado pelo AJAX em um cliente do ASP.NET que acessa o serviço

Este tópico mostra como usar o Visual Studio para criar um serviço habilitado para AJAX Windows Communication Foundation (WCF) e um cliente do ASP.NET que acessa o serviço.

## <a name="create-an-aspnet-web-app"></a>Criar um aplicativo Web ASP.NET

1. Abra o Visual Studio.

1. Dos **arquivo** menu, selecione **New** > **projeto**

1. No **novo projeto** caixa de diálogo, expanda o **instalado** > **Visual C#** > **Web** categoria e, em seguida, Selecione **aplicativo Web ASP.NET (.NET Framework)**.

1. Nomeie o projeto **SandwichServices** e clique em **Okey**.

1. No **novo aplicativo Web ASP.NET** caixa de diálogo, selecione **vazia** e, em seguida, selecione **Okey**.

   ![Diálogo do tipo de aplicativo do ASP.NET web no Visual Studio](media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a>Adicionar um formulário da web

1. Clique com botão direito no projeto SandwichServices no **Gerenciador de soluções** e selecione **Add** > **Novo Item**.

1. No **Adicionar Novo Item** caixa de diálogo, expanda o **instalado** > **Visual C#** > **Web** categoria e, em seguida, Selecione o **Web Form** modelo.

1. Aceite o nome padrão (**WebForm1**) e, em seguida, selecione **Add**.

   *WebForm1.aspx* é aberto no **origem** modo de exibição.

1. Adicione a seguinte marcação dentro de  **\<corpo >** marcas:

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a>Criar um serviço WCF habilitado pelo AJAX

1. Clique com botão direito no projeto SandwichServices no **Gerenciador de soluções** e selecione **Add** > **Novo Item**.

1. No **Adicionar Novo Item** caixa de diálogo, expanda o **instalado** > **Visual C#** > **Web** categoria e, em seguida, Selecione o **serviço do WCF (habilitado para AJAX)** modelo.

   ![Modelo de item (habilitado para AJAX) do serviço WCF no Visual Studio](media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. Nomeie o serviço **CostService** e, em seguida, selecione **Add**.

   *CostService.svc.cs* abre no editor.

1. Implemente a operação no serviço. Adicione o seguinte método à classe CostService para calcular o custo de uma quantidade de pizzas:

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a>Configurar o cliente para acessar o serviço

1. Abra o *WebForm1.aspx* do arquivo e selecione o **Design** modo de exibição.

2. Dos **modo de exibição** menu, selecione **caixa de ferramentas**.

3. Expanda o **extensões AJAX** nó e arraste e solte um **ScriptManager** para o formulário.

4. Volta a **fonte** exiba, adicione o seguinte código entre o  **\<ScriptManager >** marcas para especificar o caminho para o serviço WCF:

    ```html
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

1. Adicione o código para a função Javascript `Calculate()`. Coloque o seguinte código na **head** seção do formulário da web:

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

   Esse código chama o método de CostService para calcular o preço para três pizzas e, em seguida, exibe o resultado no período chamado **additionResult**.

## <a name="run-the-program"></a>Execute o programa

Certifique-se de que *WebForm1.aspx* tem o foco e pressione **iniciar** botão para iniciar o cliente web. O botão tem um triângulo verde e diz algo como **IIS Express (Microsoft Edge)**. Ou, você pode pressionar **F5**. Clique o **preço de 3 pizzas** botão para gerar a saída esperada do "3,75".

## <a name="example-code"></a>Exemplo de código

A seguir está o código completo na *CostService.svc.cs* arquivo:

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

A seguir está o conteúdo completo do *WebForm1.aspx* página:

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
