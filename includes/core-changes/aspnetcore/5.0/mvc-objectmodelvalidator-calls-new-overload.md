---
ms.openlocfilehash: 5083403a24a4a695d6970ef9c7a006796f41a86b
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609286"
---
### <a name="mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate"></a>MVC: ObjectModelValidator chama uma nova sobrecarga de ValidationVisitor. Validate

No ASP.NET Core 5,0, uma sobrecarga do <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType> foi adicionada. A nova sobrecarga aceita a instância de modelo de nível superior que contém propriedades:

```diff
  bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel);
+ bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container);
```

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.ObjectModelValidator> invoca essa nova sobrecarga de `ValidationVisitor` para executar a validação. Essa nova sobrecarga será pertinente se a sua biblioteca de validação se integrar com o sistema de validação de modelo do MVC ASP.NET Core.

Para obter uma discussão, consulte o problema do GitHub [dotnet/aspnetcore # 26020](https://github.com/dotnet/aspnetcore/issues/26020).

#### <a name="version-introduced"></a>Versão introduzida

5,0

#### <a name="old-behavior"></a>Comportamento antigo

`ObjectModelValidator` Invoca a seguinte sobrecarga durante a validação do modelo:

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel)
```

#### <a name="new-behavior"></a>Novo comportamento

`ObjectModelValidator` Invoca a seguinte sobrecarga durante a validação do modelo:

```csharp
ValidationVisitor.Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
```

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração foi introduzida para dar suporte a validadores, como <xref:System.ComponentModel.DataAnnotations.CompareAttribute> , que dependem da inspeção de outras propriedades.

#### <a name="recommended-action"></a>Ação recomendada

As estruturas de validação que dependem de `ObjectModelValidator` para invocar a sobrecarga existente do `ValidationVisitor` devem substituir o novo método ao direcionar o .NET 5,0 ou posterior:

```csharp
public class MyCustomValidationVisitor : ValidationVisitor
{
+  public override bool Validate(ModelMetadata metadata, string key, object model, bool alwaysValidateAtTopLevel, object container)
+  {
+    ...
}
```

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.Validate`

-->
