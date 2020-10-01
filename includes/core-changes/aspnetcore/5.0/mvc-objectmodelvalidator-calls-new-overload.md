---
ms.openlocfilehash: 5083403a24a4a695d6970ef9c7a006796f41a86b
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609286"
---
### <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a><span data-ttu-id="8194b-101">MVC: ObjectModelValidator chama uma nova sobrecarga de ValidationVisitor. Validate</span><span class="sxs-lookup"><span data-stu-id="8194b-101">MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate</span></span>

<span data-ttu-id="8194b-102">No ASP.NET Core 5,0, uma sobrecarga do <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> foi adicionada.</span><span class="sxs-lookup"><span data-stu-id="8194b-102">In ASP.NET Core 5.0, an overload of the <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> was added.</span></span> <span data-ttu-id="8194b-103">A nova sobrecarga aceita a instância de modelo de nível superior que contém propriedades:</span><span class="sxs-lookup"><span data-stu-id="8194b-103">The new overload accepts the top-level model instance that contains properties:</span></span>

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<span data-ttu-id="8194b-104"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> invoca essa nova sobrecarga de `ValidationVisitor` para executar a validação.</span><span class="sxs-lookup"><span data-stu-id="8194b-104"><xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> invokes this new overload of `ValidationVisitor` to perform validation.</span></span> <span data-ttu-id="8194b-105">Essa nova sobrecarga será pertinente se a sua biblioteca de validação se integrar com o sistema de validação de modelo do MVC ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8194b-105">This new overload is pertinent if your validation library integrates with ASP.NET Core MVC's model validation system.</span></span>

<span data-ttu-id="8194b-106">Para obter uma discussão, consulte o problema do GitHub [dotnet/aspnetcore # 26020](https://github.com/dotnet/aspnetcore/issues/26020).</span><span class="sxs-lookup"><span data-stu-id="8194b-106">For discussion, see GitHub issue [dotnet/aspnetcore#26020](https://github.com/dotnet/aspnetcore/issues/26020).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8194b-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8194b-107">Version introduced</span></span>

<span data-ttu-id="8194b-108">5,0</span><span class="sxs-lookup"><span data-stu-id="8194b-108">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8194b-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="8194b-109">Old behavior</span></span>

<span data-ttu-id="8194b-110">`ObjectModelValidator` Invoca a seguinte sobrecarga durante a validação do modelo:</span><span class="sxs-lookup"><span data-stu-id="8194b-110">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

#### <a name="new-behavior"></a><span data-ttu-id="8194b-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="8194b-111">New behavior</span></span>

<span data-ttu-id="8194b-112">`ObjectModelValidator` Invoca a seguinte sobrecarga durante a validação do modelo:</span><span class="sxs-lookup"><span data-stu-id="8194b-112">`ObjectModelValidator` invokes the following overload during model validation:</span></span>

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

#### <a name="reason-for-change"></a><span data-ttu-id="8194b-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="8194b-113">Reason for change</span></span>

<span data-ttu-id="8194b-114">Essa alteração foi introduzida para dar suporte a validadores, como <xref:System.ComponentModel.DataAnnotations.CompareAttribute> , que dependem da inspeção de outras propriedades.</span><span class="sxs-lookup"><span data-stu-id="8194b-114">This change was introduced to support validators, such as <xref:System.ComponentModel.DataAnnotations.CompareAttribute>, that rely on inspection of other properties.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8194b-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="8194b-115">Recommended action</span></span>

<span data-ttu-id="8194b-116">As estruturas de validação que dependem de `ObjectModelValidator` para invocar a sobrecarga existente do `ValidationVisitor` devem substituir o novo método ao direcionar o .NET 5,0 ou posterior:</span><span class="sxs-lookup"><span data-stu-id="8194b-116">Validation frameworks that rely on `ObjectModelValidator` to invoke the existing overload of `ValidationVisitor` must override the new method when targeting .NET 5.0 or later:</span></span>

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

#### <a name="category"></a><span data-ttu-id="8194b-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="8194b-117">Category</span></span>

<span data-ttu-id="8194b-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8194b-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8194b-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8194b-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
