---
title: Como usar propriedades indexadas em programação de interoperabilidade COM – guia de programação C#
description: Saiba como as propriedades indexadas melhoram a maneira como as propriedades COM têm parâmetros são consumidas neste exemplo de C#.
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: abd785864bd79d455024cb4501c76a21b349aa91
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303004"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="3f679-103">Como usar propriedades indexadas em programação de interoperabilidade COM (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="3f679-103">How to use indexed properties in COM interop programming (C# Programming Guide)</span></span>
<span data-ttu-id="3f679-104">As *propriedades indexadas* melhoram a maneira na qual as propriedades COM que têm parâmetros são consumidas na programação em C#.</span><span class="sxs-lookup"><span data-stu-id="3f679-104">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="3f679-105">As propriedades indexadas trabalham juntamente com outras funcionalidades no Visual C#, como [argumentos nomeados e opcionais](../classes-and-structs/named-and-optional-arguments.md), um novo tipo ([dinâmico](../../language-reference/builtin-types/reference-types.md)) e [informações de tipo inseridas](../../../standard/assembly/embed-types-visual-studio.md) para melhorar a programação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="3f679-105">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/builtin-types/reference-types.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="3f679-106">Nas versões anteriores do C#, os métodos são acessíveis como propriedades apenas se o método `get` não tem parâmetros e o método `set` tem apenas um parâmetro de valor.</span><span class="sxs-lookup"><span data-stu-id="3f679-106">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="3f679-107">No entanto, nem todas as propriedades COM atendem a essas restrições.</span><span class="sxs-lookup"><span data-stu-id="3f679-107">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="3f679-108">Por exemplo, a propriedade <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> do Excel tem um acessador `get` que requer um parâmetro para o nome do intervalo.</span><span class="sxs-lookup"><span data-stu-id="3f679-108">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="3f679-109">No passado, como não era possível acessar a propriedade `Range` diretamente, era necessário usar o método `get_Range` em vez disso, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3f679-109">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="3f679-110">Em vez disso, as propriedades indexadas permitem escrever o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3f679-110">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="3f679-111">O exemplo anterior também usa o recurso [argumentos opcionais](../classes-and-structs/named-and-optional-arguments.md), que permite que você omita `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="3f679-111">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="3f679-112">Da mesma forma, para definir o valor da propriedade `Value` de um objeto <xref:Microsoft.Office.Interop.Excel.Range> no C# 3.0 e versões anteriores, são necessários dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="3f679-112">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="3f679-113">Um fornece um argumento para um parâmetro opcional que especifica o tipo do valor de intervalo.</span><span class="sxs-lookup"><span data-stu-id="3f679-113">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="3f679-114">O outro fornece o valor para a propriedade `Value`.</span><span class="sxs-lookup"><span data-stu-id="3f679-114">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="3f679-115">Os exemplos a seguir ilustram essas técnicas.</span><span class="sxs-lookup"><span data-stu-id="3f679-115">The following examples illustrate these techniques.</span></span> <span data-ttu-id="3f679-116">Ambos definem o valor da célula A1 como `Name`.</span><span class="sxs-lookup"><span data-stu-id="3f679-116">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="3f679-117">Em vez disso, as propriedades indexadas permitem escrever o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="3f679-117">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="3f679-118">Não é possível criar propriedades indexadas de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="3f679-118">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="3f679-119">O recurso dá suporte apenas ao consumo de propriedades indexadas existentes.</span><span class="sxs-lookup"><span data-stu-id="3f679-119">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f679-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f679-120">Example</span></span>  
 <span data-ttu-id="3f679-121">O código a seguir mostra um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="3f679-121">The following code shows a complete example.</span></span> <span data-ttu-id="3f679-122">Para obter mais informações sobre como configurar um projeto que acessa a API do Office, consulte [como acessar objetos de interoperabilidade do Office usando os recursos do C#](./how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="3f679-122">For more information about how to set up a project that accesses the Office API, see [How to access Office interop objects by using C# features](./how-to-access-office-onterop-objects.md).</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3f679-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="3f679-123">See also</span></span>

- [<span data-ttu-id="3f679-124">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="3f679-124">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="3f679-125">dinâmico</span><span class="sxs-lookup"><span data-stu-id="3f679-125">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="3f679-126">Usando o tipo dynamic</span><span class="sxs-lookup"><span data-stu-id="3f679-126">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="3f679-127">Como usar argumentos nomeados e opcionais na programação do Office</span><span class="sxs-lookup"><span data-stu-id="3f679-127">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="3f679-128">Como acessar objetos de interoperabilidade do Office usando recursos do C#</span><span class="sxs-lookup"><span data-stu-id="3f679-128">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="3f679-129">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="3f679-129">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
