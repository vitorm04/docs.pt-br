---
title: Classe ControlBuilderInterceptor
ms.date: 08/11/2020
api_name:
- System.Web.Compilation.ControlBuilderInterceptor
api_location:
- System.Web.dll
api_type:
- Assembly
topic_type:
- apiref
ms.openlocfilehash: 312d977f832d262b1bebc6638280b67b133babdf
ms.sourcegitcommit: 70d6a7e4f7187cbfa332f0f8be76566f7828cfcd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88084390"
---
# <a name="controlbuilderinterceptor-class"></a><span data-ttu-id="f454c-102">Classe ControlBuilderInterceptor</span><span class="sxs-lookup"><span data-stu-id="f454c-102">ControlBuilderInterceptor class</span></span>

<span data-ttu-id="f454c-103">A `ControlBuilderInterceptor` classe permite que o processo de compilação seja personalizado ou controlado.</span><span class="sxs-lookup"><span data-stu-id="f454c-103">The `ControlBuilderInterceptor` class allows the compilation process to be customized or controlled.</span></span>

## <a name="syntax"></a><span data-ttu-id="f454c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f454c-104">Syntax</span></span>

```csharp
internal class ControlBuilderInterceptor
```

> [!WARNING]
> <span data-ttu-id="f454c-105">A `ControlBuilderInterceptor` classe é interna e não deve ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="f454c-105">The `ControlBuilderInterceptor` class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="f454c-106">Conforme descrito na seção comentários, a existência desse tipo pode ser verificada para determinar se o suporte ao tipo de interceptador está presente.</span><span class="sxs-lookup"><span data-stu-id="f454c-106">As described in the Remarks section, the existence of this type can be checked to determine whether interceptor type support is present.</span></span> <span data-ttu-id="f454c-107">A Microsoft não oferece suporte a nenhum outro uso dessa classe em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="f454c-107">Microsoft does not support any other use of this class in a production application under any circumstance.</span></span>

## <a name="remarks"></a><span data-ttu-id="f454c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="f454c-108">Remarks</span></span>

<span data-ttu-id="f454c-109">No .NET Framework 2,0 e .NET Framework 3,5, as atualizações de [agosto de 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) adicionaram suporte para o uso de um tipo de interceptador para personalizar ou controlar o processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="f454c-109">In .NET Framework 2.0 and .NET Framework 3.5, the [August 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug) updates added support for using an interceptor type to customize or control the compilation process.</span></span> <span data-ttu-id="f454c-110">Você pode determinar se esse suporte está presente usando o <xref:System.Type.GetType?displayProperty=nameWithType> para verificar a existência do `ControlBuilderInterceptor` tipo, conforme demonstrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f454c-110">You can determine whether this support is present by using <xref:System.Type.GetType?displayProperty=nameWithType> to check the existence of the `ControlBuilderInterceptor` type, as demonstrated in the following code.</span></span>

```csharp
Type type = Type.GetType("System.Web.Compilation.ControlBuilderInterceptor, System.Web, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a");
```

<span data-ttu-id="f454c-111">Se o valor de retorno for não nulo, o suporte ao Interceptor estará presente.</span><span class="sxs-lookup"><span data-stu-id="f454c-111">If the return value is non-null, then interceptor support is present.</span></span> <span data-ttu-id="f454c-112">Se o valor de retorno for `null` , ou se uma exceção for lançada, as atualizações de agosto de 2020 não foram instaladas e o suporte ao Interceptor está ausente.</span><span class="sxs-lookup"><span data-stu-id="f454c-112">If the return value is `null`, or if an exception is thrown, then the August 2020 updates have not been installed, and interceptor support is absent.</span></span>

<span data-ttu-id="f454c-113">Se o suporte ao Interceptor estiver presente, você poderá gravar e registrar um tipo de interceptador que irá interagir com o processo de compilação exatamente da mesma forma que o <xref:System.Web.Compilation.ControlBuilderInterceptor> faz em versões posteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f454c-113">If interceptor support is present, you can write and register an interceptor type that will interact with the compilation process in exactly the same way that <xref:System.Web.Compilation.ControlBuilderInterceptor> does on later versions of .NET Framework.</span></span> <span data-ttu-id="f454c-114">No .NET Framework 2,0 e .NET Framework 3,5, o tipo de interceptador pode ser qualquer classe que atenda aos seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="f454c-114">In .NET Framework 2.0 and .NET Framework 3.5, the interceptor type can be any class that meets the following requirements:</span></span>

* <span data-ttu-id="f454c-115">Tem um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f454c-115">Has a public, parameterless constructor.</span></span>
* <span data-ttu-id="f454c-116">Tem métodos públicos e não estáticos chamados `PreControlBuilderInit` e `OnProcessGeneratedCode` que têm a mesma assinatura e semântica que os <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> métodos e <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> , que existem em versões posteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f454c-116">Has public, non-static methods named `PreControlBuilderInit` and `OnProcessGeneratedCode` that have the same signature and semantics as the <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> and <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> methods, which exist in later versions of .NET Framework.</span></span>

<span data-ttu-id="f454c-117">Registre o tipo de interceptador usando a `aspnet:20ControlBuilderInterceptor` chave em configurações do aplicativo ASP.net ( `<appSettings>` ).</span><span class="sxs-lookup"><span data-stu-id="f454c-117">Register the interceptor type by using the `aspnet:20ControlBuilderInterceptor` key in ASP.NET application settings (`<appSettings>`).</span></span> <span data-ttu-id="f454c-118">Essa configuração de aplicativo deve estar listada no computador ou no arquivo de *web.config* do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f454c-118">This application setting must be listed in your computer or application *web.config* file.</span></span> <span data-ttu-id="f454c-119">Especifique o tipo de interceptador usando seu nome de tipo qualificado por assembly.</span><span class="sxs-lookup"><span data-stu-id="f454c-119">Specify the interceptor type by using its assembly-qualified type name.</span></span> <span data-ttu-id="f454c-120">O exemplo a seguir mostra como registrar um tipo de interceptador chamado `Fabrikam.Interceptor` .</span><span class="sxs-lookup"><span data-stu-id="f454c-120">The following example shows how to register an interceptor type named `Fabrikam.Interceptor`.</span></span>

```xml
<configuration>
  ...
  <appSettings>
    ...
    <add key="aspnet:20ControlBuilderInterceptor"
         value="Fabrikam.Interceptor, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
  </appSettings>
</configuration>

To retrieve the assembly-qualified name of a type, use the <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> property, as demonstrated in the following code.

```csharp
string assemblyQualifiedName = typeof(Fabrikam.Interceptor).AssemblyQualifiedName;
```

<span data-ttu-id="f454c-121">Quando o suporte ao Interceptor está presente, o processo de compilação interage com o tipo listado da maneira descrita acima.</span><span class="sxs-lookup"><span data-stu-id="f454c-121">When interceptor support is present, the compilation process interacts with the listed type in the manner described above.</span></span> <span data-ttu-id="f454c-122">Quando o suporte ao Interceptor está ausente, a configuração do aplicativo é ignorada e não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="f454c-122">When interceptor support is absent, the application setting is ignored and has no effect.</span></span>

## <a name="requirements"></a><span data-ttu-id="f454c-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f454c-123">Requirements</span></span>

<span data-ttu-id="f454c-124">**Namespace:** System. Web. Compilation</span><span class="sxs-lookup"><span data-stu-id="f454c-124">**Namespace:** System.Web.Compilation</span></span>

<span data-ttu-id="f454c-125">**Assembly:** System. Web (em System.Web.dll)</span><span class="sxs-lookup"><span data-stu-id="f454c-125">**Assembly:** System.Web (in System.Web.dll)</span></span>

<span data-ttu-id="f454c-126">**Versões do .NET Framework:** 3,5, 2,0</span><span class="sxs-lookup"><span data-stu-id="f454c-126">**.NET Framework versions:** 3.5, 2.0</span></span>
