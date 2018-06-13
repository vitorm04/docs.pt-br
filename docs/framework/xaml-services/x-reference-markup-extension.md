---
title: Extensão de marcação x:Reference
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: 960f5c0e4192df72090c1a571dfc2fc5e3fd8ba3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562239"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="c3dfe-102">Extensão de marcação x:Reference</span><span class="sxs-lookup"><span data-stu-id="c3dfe-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="c3dfe-103">Faz referência a uma instância que é declarada em outro lugar na marcação XAML.</span><span class="sxs-lookup"><span data-stu-id="c3dfe-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="c3dfe-104">A referência a um elemento `x:Name`.</span><span class="sxs-lookup"><span data-stu-id="c3dfe-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c3dfe-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="c3dfe-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="c3dfe-106">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="c3dfe-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c3dfe-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="c3dfe-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="c3dfe-108">O `x:Name` valor (ou valor da <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identificado propriedade) da instância referenciada.</span><span class="sxs-lookup"><span data-stu-id="c3dfe-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3dfe-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3dfe-109">Remarks</span></span>  
 <span data-ttu-id="c3dfe-110">`x:Reference` fornece suporte de nível de linguagem XAML para um conceito de referência de elemento caso contrário, foi implementado em estruturas específicas, como WPF.</span><span class="sxs-lookup"><span data-stu-id="c3dfe-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="c3dfe-111">x: referência e WPF</span><span class="sxs-lookup"><span data-stu-id="c3dfe-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="c3dfe-112">No WPF e XAML 2006, referências de elemento são endereçadas pelo recurso de nível da estrutura de <xref:System.Windows.Data.Binding.ElementName%2A> associação.</span><span class="sxs-lookup"><span data-stu-id="c3dfe-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="c3dfe-113">Para a maioria dos aplicativos do WPF e cenários, <xref:System.Windows.Data.Binding.ElementName%2A> associação ainda deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="c3dfe-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="c3dfe-114">Exceções a essa orientação geral podem incluir casos onde não há contexto de dados ou outras considerações de escopo que tornarem a associação de dados impraticável e compilação de marcação não estiver envolvida.</span><span class="sxs-lookup"><span data-stu-id="c3dfe-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="c3dfe-115">`x:Reference` uma construção é definida em XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="c3dfe-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="c3dfe-116">No WPF, você pode usar os recursos de XAML 2009, mas apenas para XAML que não é compilado marcação do WPF.</span><span class="sxs-lookup"><span data-stu-id="c3dfe-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="c3dfe-117">Compilação de marcação XAML e o formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de linguagem XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="c3dfe-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
