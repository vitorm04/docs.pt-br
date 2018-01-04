---
title: Diretiva x:Members
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e76f539e713f3d21751de18c86cc2dcebf99f570
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xmembers-directive"></a><span data-ttu-id="03579-102">Diretiva x:Members</span><span class="sxs-lookup"><span data-stu-id="03579-102">x:Members Directive</span></span>
<span data-ttu-id="03579-103">Contém um conjunto de membros que estão definidos na marcação, que se aplicam à classe: x do elemento pai.</span><span class="sxs-lookup"><span data-stu-id="03579-103">Holds a set of members that are defined in markup, which apply to the x:Class of the parent element.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="03579-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="03579-104">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="03579-105">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="03579-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`className`|<span data-ttu-id="03579-106">Nome da classe de backup ou classe parcial para a produção de XAML.</span><span class="sxs-lookup"><span data-stu-id="03579-106">Name of the backing class or partial class for the XAML production.</span></span> <span data-ttu-id="03579-107">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="03579-107">See Remarks.</span></span>|  
|`oneOrMoreMembers`|<span data-ttu-id="03579-108">Um ou mais elementos de objeto que representa as definições de membro.</span><span class="sxs-lookup"><span data-stu-id="03579-108">One or more object elements that represent member definitions.</span></span> <span data-ttu-id="03579-109">Normalmente, esses são `x:Property` elementos de objeto.</span><span class="sxs-lookup"><span data-stu-id="03579-109">Typically, these are `x:Property` object elements.</span></span> <span data-ttu-id="03579-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="03579-110">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03579-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="03579-111">Remarks</span></span>  
 <span data-ttu-id="03579-112">Na implementação de serviços XAML do .NET Framework, não há backup classe ou implementação subjacente do membro para `x:Members`.</span><span class="sxs-lookup"><span data-stu-id="03579-112">In the .NET Framework XAML Services implementation, there is no backing class or underlying member implementation for `x:Members`.</span></span> <span data-ttu-id="03579-113">`x:Members`é um membro XAML especial que pode existir como um membro em qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="03579-113">`x:Members` is a special XAML member that can exist as a member on any type.</span></span> <span data-ttu-id="03579-114">Em um fluxo do nó XAML, `x:Members` é representado como um membro chamado `Members`, do namespace XAML de linguagem XAML.</span><span class="sxs-lookup"><span data-stu-id="03579-114">In a XAML node stream, `x:Members` is represented as a member named `Members`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="03579-115">O membro `Members` contém uma lista somente leitura genérica de `Member` objetos.</span><span class="sxs-lookup"><span data-stu-id="03579-115">The member `Members` contains a read-only generic list of `Member` objects.</span></span> <span data-ttu-id="03579-116">Na marcação típica, os membros individuais são especificados como `x:Property` elementos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="03579-116">In typical markup the individual members are specified as `x:Property` property elements.</span></span> <span data-ttu-id="03579-117">`x:Property`é um tipo mais preciso especificamente para propriedades de tipos e pode ser atribuído a `x:Member`.</span><span class="sxs-lookup"><span data-stu-id="03579-117">`x:Property` is a more precise type specifically for properties of types and is assignable to `x:Member`.</span></span> <span data-ttu-id="03579-118">Para obter mais informações, consulte [diretiva X:property](../../../docs/framework/xaml-services/x-property-directive.md).</span><span class="sxs-lookup"><span data-stu-id="03579-118">For more information, see [x:Property Directive](../../../docs/framework/xaml-services/x-property-directive.md).</span></span>  
  
 <span data-ttu-id="03579-119">Para dar suporte a um uso prático de `x:Members` como um meio para especificar definições de membro na marcação, os membros devem ser associados uma classe que pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="03579-119">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="03579-120">O modelo desejado é que `x:Members` existe como um membro de um tipo que especifica um `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="03579-120">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="03579-121">No entanto, o mecanismo para a associação de tipos e membros ou para a produção de definições de membro dinâmico não tem suporte no nível de serviços XAML do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03579-121">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="03579-122">Isso é da esquerda para estruturas individuais que têm modelos de aplicativos que dão suporte a definições de membro de XAML.</span><span class="sxs-lookup"><span data-stu-id="03579-122">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="03579-123">Normalmente, as ações de compilação MSBUILD que a compilação de marcação XAML e um integração-lo com code-behind ou produzir somente de XAML assemblies são necessários para dar suporte a esse recurso.</span><span class="sxs-lookup"><span data-stu-id="03579-123">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>  
  
## <a name="xmembers-for-windows-workflow-foundation"></a><span data-ttu-id="03579-124">x: membros para Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="03579-124">x:Members for Windows Workflow Foundation</span></span>  
 <span data-ttu-id="03579-125">Para Windows Workflow Foundation, `x:Members` contém os membros de uma atividade personalizada composta inteiramente em XAML ou XAML – definido membros dinâmicos para um designer de atividade com code-behind.</span><span class="sxs-lookup"><span data-stu-id="03579-125">For Windows Workflow Foundation, `x:Members` contains the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="03579-126">`x:Class`também deve ser especificado no elemento raiz da produção XAML.</span><span class="sxs-lookup"><span data-stu-id="03579-126">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="03579-127">Isso não é um requisito no nível de serviços XAML do .NET Framework, mas se torna um requisito quando a produção de XAML é carregada pelas ações de compilação do MSBUILD que dão suporte a atividades personalizadas e XAML do Windows Workflow Foundation em geral.</span><span class="sxs-lookup"><span data-stu-id="03579-127">This is not a requirement at the .NET Framework XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="03579-128">`x:Members`deve ser o primeiro elemento filho na marcação do elemento de objeto que declara o `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="03579-128">`x:Members` must be the first child element in markup of the object element that declares the `x:Class`.</span></span>
