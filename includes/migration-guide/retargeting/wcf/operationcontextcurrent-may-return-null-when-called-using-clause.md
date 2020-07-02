---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614289"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a><span data-ttu-id="8279e-101">OperationContext.Current pode retornar nulo quando chamado usando cláusula</span><span class="sxs-lookup"><span data-stu-id="8279e-101">OperationContext.Current may return null when called in a using clause</span></span>

#### <a name="details"></a><span data-ttu-id="8279e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8279e-102">Details</span></span>

<span data-ttu-id="8279e-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> poderá retornar `null` e um <xref:System.NullReferenceException> poderá ocorrer quando todas as seguintes condições forem verdadeiras:</span><span class="sxs-lookup"><span data-stu-id="8279e-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> may return `null` and a <xref:System.NullReferenceException> may result if all of the following conditions are true:</span></span>

- <span data-ttu-id="8279e-104">Você recupera o valor da propriedade <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> em um método que retorna um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="8279e-104">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property in a method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>
- <span data-ttu-id="8279e-105">Você cria uma instância do objeto <xref:System.ServiceModel.OperationContextScope> em uma cláusula `using`.</span><span class="sxs-lookup"><span data-stu-id="8279e-105">You instantiate the <xref:System.ServiceModel.OperationContextScope> object in a `using` clause.</span></span>
- <span data-ttu-id="8279e-106">Você recupera o valor da propriedade <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> dentro de `using statement`.</span><span class="sxs-lookup"><span data-stu-id="8279e-106">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property within the `using statement`.</span></span> <span data-ttu-id="8279e-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8279e-107">For example:</span></span>

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a><span data-ttu-id="8279e-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8279e-108">Suggestion</span></span>

<span data-ttu-id="8279e-109">Para solucionar esse problema, você pode fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8279e-109">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="8279e-110">Modifique seu código da seguinte maneira para instanciar um novo não `null` <xref:System.ServiceModel.OperationContext.Current%2A> objeto:</span><span class="sxs-lookup"><span data-stu-id="8279e-110">Modify your code as follows to instantiate a new non- `null` <xref:System.ServiceModel.OperationContext.Current%2A> object:</span></span>

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- <span data-ttu-id="8279e-111">Instalar a atualização mais recente do .NET Framework 4.6.2 ou atualizar para uma versão posterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8279e-111">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="8279e-112">Isso desabilita o fluxo do <xref:System.Threading.ExecutionContext> em <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> e restaura o comportamento de aplicativos do WCF no .NET Framework 4.6.1 e em versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="8279e-112">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> and restores the behavior of WCF applications in the .NET Framework 4.6.1 and earlier versions.</span></span> <span data-ttu-id="8279e-113">Esse comportamento é configurável; é equivalente a adicionar a seguinte configuração de aplicativo ao arquivo de configuração:</span><span class="sxs-lookup"><span data-stu-id="8279e-113">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    <span data-ttu-id="8279e-114">Se essa alteração for indesejável e seu aplicativo depender do fluxo do contexto de execução entre contextos de operação, você poderá habilitar o fluxo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8279e-114">If this change is undesirable and your application depends on execution context flowing between operation contexts, you can enable its flow as follows:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| <span data-ttu-id="8279e-115">Name</span><span class="sxs-lookup"><span data-stu-id="8279e-115">Name</span></span>    | <span data-ttu-id="8279e-116">Valor</span><span class="sxs-lookup"><span data-stu-id="8279e-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8279e-117">Escopo</span><span class="sxs-lookup"><span data-stu-id="8279e-117">Scope</span></span>   | <span data-ttu-id="8279e-118">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="8279e-118">Edge</span></span>        |
| <span data-ttu-id="8279e-119">Versão</span><span class="sxs-lookup"><span data-stu-id="8279e-119">Version</span></span> | <span data-ttu-id="8279e-120">4.6.2</span><span class="sxs-lookup"><span data-stu-id="8279e-120">4.6.2</span></span>       |
| <span data-ttu-id="8279e-121">Type</span><span class="sxs-lookup"><span data-stu-id="8279e-121">Type</span></span>    | <span data-ttu-id="8279e-122">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="8279e-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8279e-123">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8279e-123">Affected APIs</span></span>

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
