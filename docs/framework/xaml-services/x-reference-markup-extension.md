---
title: "Extensão de marcação x:Reference"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 06e59e7686004f8fd44473bd9572ed07a0118d1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="da812-102">Extensão de marcação x:Reference</span><span class="sxs-lookup"><span data-stu-id="da812-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="da812-103">Faz referência a uma instância que é declarada em outro lugar na marcação XAML.</span><span class="sxs-lookup"><span data-stu-id="da812-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="da812-104">A referência a um elemento `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="da812-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="da812-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="da812-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="da812-106">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="da812-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="da812-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="da812-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="da812-108">O `x:Name` valor (ou valor da <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identificado propriedade) da instância referenciada.</span><span class="sxs-lookup"><span data-stu-id="da812-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da812-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="da812-109">Remarks</span></span>  
 <span data-ttu-id="da812-110">`x:Reference`fornece suporte de nível de linguagem XAML para um conceito de referência de elemento caso contrário, foi implementado em estruturas específicas, como WPF.</span><span class="sxs-lookup"><span data-stu-id="da812-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="da812-111">x: referência e WPF</span><span class="sxs-lookup"><span data-stu-id="da812-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="da812-112">No WPF e XAML 2006, referências de elemento são endereçadas pelo recurso de nível da estrutura de <xref:System.Windows.Data.Binding.ElementName%2A> associação.</span><span class="sxs-lookup"><span data-stu-id="da812-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="da812-113">Para a maioria dos aplicativos do WPF e cenários, <xref:System.Windows.Data.Binding.ElementName%2A> associação ainda deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="da812-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="da812-114">Exceções a essa orientação geral podem incluir casos onde não há contexto de dados ou outras considerações de escopo que tornarem a associação de dados impraticável e compilação de marcação não estiver envolvida.</span><span class="sxs-lookup"><span data-stu-id="da812-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="da812-115">`x:Reference`uma construção é definida em XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="da812-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="da812-116">No WPF, você pode usar os recursos de XAML 2009, mas apenas para XAML que não é compilado marcação do WPF.</span><span class="sxs-lookup"><span data-stu-id="da812-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="da812-117">Compilação de marcação XAML e o formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de linguagem XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="da812-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
