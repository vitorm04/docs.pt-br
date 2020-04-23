---
title: Diretiva x:Property
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 2804ec935d0626cba9ef050f70a3266cf23bcce0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071405"
---
# <a name="xproperty-directive"></a><span data-ttu-id="96b77-102">Diretiva x:Property</span><span class="sxs-lookup"><span data-stu-id="96b77-102">x:Property Directive</span></span>

<span data-ttu-id="96b77-103">Declara uma propriedade XAML na marcação.</span><span class="sxs-lookup"><span data-stu-id="96b77-103">Declares a XAML property in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="96b77-104">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="96b77-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="96b77-105">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="96b77-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="96b77-106">Nome da classe de apoio ou classe parcial para a produção xaml.</span><span class="sxs-lookup"><span data-stu-id="96b77-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`propertyName`|<span data-ttu-id="96b77-107">Nome do membro da propriedade que está sendo definido.</span><span class="sxs-lookup"><span data-stu-id="96b77-107">Member name of the property being defined.</span></span>|
|`propertyType`|<span data-ttu-id="96b77-108">Nome de tipo (ou outro formulário de string, específico da estrutura) que especifica o tipo desta propriedade.</span><span class="sxs-lookup"><span data-stu-id="96b77-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|

## <a name="remarks"></a><span data-ttu-id="96b77-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="96b77-109">Remarks</span></span>

<span data-ttu-id="96b77-110">Na implementação do .NET XAML Services, .</span><span class="sxs-lookup"><span data-stu-id="96b77-110">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="96b77-111">`x:Property`não tem um tipo direto de apoio, <xref:System.Windows.Markup.PropertyDefinition> mas é suportado pela classe.</span><span class="sxs-lookup"><span data-stu-id="96b77-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="96b77-112">Em um fluxo de nó `x:Property` XAML, um `Property`elemento é representado como um membro chamado , a partir do espaço de nome XAML.</span><span class="sxs-lookup"><span data-stu-id="96b77-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="96b77-113">O `Property` membro tem atributos declarados por marcação.</span><span class="sxs-lookup"><span data-stu-id="96b77-113">The member `Property` hold attributes as declared by markup.</span></span>

<span data-ttu-id="96b77-114">O significado `Name` `Type` de e não são atribuídos ao nível de Serviços .NET XAML.</span><span class="sxs-lookup"><span data-stu-id="96b77-114">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="96b77-115">Eles são armazenados no fluxo inicial do nó XAML como valores de seqüência, a serem interpretados posteriormente sob as regras que podem ser impostas por estruturas específicas.</span><span class="sxs-lookup"><span data-stu-id="96b77-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="96b77-116">O significado pode se alinhar a um nome XAML e ao significado do tipo XAML, ou pode ser válido apenas em um sistema de tipo de backup, dependendo da implementação.</span><span class="sxs-lookup"><span data-stu-id="96b77-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="96b77-117">Para apoiar um `x:Members` uso prático de como um meio de especificar definições de membros na marcação, os membros devem ser associados a uma classe que pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="96b77-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="96b77-118">O modelo pretendido `x:Members` é que existe como um `x:Class`membro de um tipo que especifica um .</span><span class="sxs-lookup"><span data-stu-id="96b77-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="96b77-119">No entanto, o mecanismo para associar tipos e membros ou para produzir definições dinâmicas de membros não é suportado no nível de Serviços .NET XAML.</span><span class="sxs-lookup"><span data-stu-id="96b77-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="96b77-120">Isso é deixado para estruturas individuais que têm modelos de aplicativos que suportam definições de membros a partir de XAML.</span><span class="sxs-lookup"><span data-stu-id="96b77-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="96b77-121">Normalmente, o MSBUILD constrói ações que compilam o XAML e o integram com o código-atrás ou produzem conjuntos puros de XAML para suportar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="96b77-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="96b77-122">x:Propriedade para Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="96b77-122">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="96b77-123">Para o Windows `x:Property` Workflow Foundation, define os membros de uma atividade personalizada composta inteiramente em XAML, ou XAML – membros dinâmicos definidos para um designer de atividades com código atrás.</span><span class="sxs-lookup"><span data-stu-id="96b77-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="96b77-124">`x:Class`também deve ser especificado no elemento raiz da produção XAML.</span><span class="sxs-lookup"><span data-stu-id="96b77-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="96b77-125">Isso não é um requisito no nível de Serviços XAML .NET, mas se torna um requisito quando a produção XAML é carregada pelas ações de compilação do MSBUILD que suportam atividades personalizadas e o Windows Workflow Foundation XAML em geral.</span><span class="sxs-lookup"><span data-stu-id="96b77-125">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="96b77-126">O Windows Workflow Foundation não usa o nome do tipo `x:Property` `Type` XAML puro como seu valor pretendido para o atributo e, em vez disso, usa uma convenção que não está documentada aqui.</span><span class="sxs-lookup"><span data-stu-id="96b77-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="96b77-127">Para obter mais informações, consulte [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="96b77-127">For more information, see [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
