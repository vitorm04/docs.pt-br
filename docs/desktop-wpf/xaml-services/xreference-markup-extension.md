---
title: Extensão de marcação x:Reference
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071377"
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="a549a-102">Extensão de marcação x:Reference</span><span class="sxs-lookup"><span data-stu-id="a549a-102">x:Reference Markup Extension</span></span>

<span data-ttu-id="a549a-103">Faz referência a uma instância que é declarada em outro lugar na marcação XAML.</span><span class="sxs-lookup"><span data-stu-id="a549a-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="a549a-104">A referência refere-se a `x:Name`um elemento.</span><span class="sxs-lookup"><span data-stu-id="a549a-104">The reference refers to an element's `x:Name`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="a549a-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="a549a-105">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Reference instancexName}" .../>
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="a549a-106">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="a549a-106">XAML Object Element Usage</span></span>

```xaml
<object>
  <object.property>
    <x:Reference Name="instancexName"/>
  </object.property>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="a549a-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="a549a-107">XAML Values</span></span>

|||
|-|-|
|`instancexName`|<span data-ttu-id="a549a-108">O `x:Name` valor (ou <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>valor da propriedade -identificada) da instância referenciada.</span><span class="sxs-lookup"><span data-stu-id="a549a-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a549a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a549a-109">Remarks</span></span>

<span data-ttu-id="a549a-110">`x:Reference`fornece suporte em nível de linguagem XAML para um conceito de referência de elemento que foi implementado de outra forma em estruturas específicas, como o WPF.</span><span class="sxs-lookup"><span data-stu-id="a549a-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>

## <a name="xreference-and-wpf"></a><span data-ttu-id="a549a-111">x:Referência e WPF</span><span class="sxs-lookup"><span data-stu-id="a549a-111">x:Reference and WPF</span></span>

<span data-ttu-id="a549a-112">No WPF e no XAML 2006, as referências dos <xref:System.Windows.Data.Binding.ElementName%2A> elementos são abordadas pelo recurso de nível de estrutura da vinculação.</span><span class="sxs-lookup"><span data-stu-id="a549a-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="a549a-113">Para a maioria dos aplicativos <xref:System.Windows.Data.Binding.ElementName%2A> e cenários do WPF, a vinculação ainda deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="a549a-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="a549a-114">Exceções a esta orientação geral podem incluir casos em que há contexto de dados ou outras considerações de escopo que tornam a vinculação de dados impraticável e onde a compilação de marcação não está envolvida.</span><span class="sxs-lookup"><span data-stu-id="a549a-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>

<span data-ttu-id="a549a-115">`x:Reference`é uma construção definida em XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="a549a-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="a549a-116">No WPF, você pode usar os recursos do XAML 2009, mas apenas para XAML que não é compilado por marcação WPF.</span><span class="sxs-lookup"><span data-stu-id="a549a-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="a549a-117">O XAML compilado por marcação e a forma BAML de XAML não suportam atualmente as palavras-chave e recursos do idioma XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="a549a-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
