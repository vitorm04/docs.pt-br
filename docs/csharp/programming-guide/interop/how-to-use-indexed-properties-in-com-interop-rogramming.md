---
title: 'Como: usar propriedades indexadas na programação para interoperabilidade COM – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: f1be14ad7ddb6973cc89f10c1735ba2ebce13f97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971655"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="3af00-102">Como: usar propriedades indexadas na programação para interoperabilidade COM (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="3af00-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="3af00-103">As *propriedades indexadas* melhoram a maneira na qual as propriedades COM que têm parâmetros são consumidas na programação em C#.</span><span class="sxs-lookup"><span data-stu-id="3af00-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="3af00-104">As propriedades indexadas trabalham juntamente com outras funcionalidades no Visual C#, como [argumentos nomeados e opcionais](../classes-and-structs/named-and-optional-arguments.md), um novo tipo ([dinâmico](../../language-reference/keywords/dynamic.md)) e [informações de tipo inseridas](../../../standard/assembly/embed-types-visual-studio.md) para melhorar a programação do Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="3af00-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/keywords/dynamic.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="3af00-105">Nas versões anteriores do C#, os métodos são acessíveis como propriedades apenas se o método `get` não tem parâmetros e o método `set` tem apenas um parâmetro de valor.</span><span class="sxs-lookup"><span data-stu-id="3af00-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="3af00-106">No entanto, nem todas as propriedades COM atendem a essas restrições.</span><span class="sxs-lookup"><span data-stu-id="3af00-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="3af00-107">Por exemplo, a propriedade <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> do Excel tem um acessador `get` que requer um parâmetro para o nome do intervalo.</span><span class="sxs-lookup"><span data-stu-id="3af00-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="3af00-108">No passado, como não era possível acessar a propriedade `Range` diretamente, era necessário usar o método `get_Range` em vez disso, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3af00-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="3af00-109">Em vez disso, as propriedades indexadas permitem escrever o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3af00-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="3af00-110">O exemplo anterior também usa o recurso [argumentos opcionais](../classes-and-structs/named-and-optional-arguments.md), que permite que você omita `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="3af00-110">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="3af00-111">Da mesma forma, para definir o valor da propriedade `Value` de um objeto <xref:Microsoft.Office.Interop.Excel.Range> no C# 3.0 e versões anteriores, são necessários dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="3af00-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="3af00-112">Um fornece um argumento para um parâmetro opcional que especifica o tipo do valor de intervalo.</span><span class="sxs-lookup"><span data-stu-id="3af00-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="3af00-113">O outro fornece o valor para a propriedade `Value`.</span><span class="sxs-lookup"><span data-stu-id="3af00-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="3af00-114">Os exemplos a seguir ilustram essas técnicas.</span><span class="sxs-lookup"><span data-stu-id="3af00-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="3af00-115">Ambos definem o valor da célula A1 como `Name`.</span><span class="sxs-lookup"><span data-stu-id="3af00-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="3af00-116">Em vez disso, as propriedades indexadas permitem escrever o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="3af00-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="3af00-117">Não é possível criar propriedades indexadas de sua preferência.</span><span class="sxs-lookup"><span data-stu-id="3af00-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="3af00-118">O recurso dá suporte apenas ao consumo de propriedades indexadas existentes.</span><span class="sxs-lookup"><span data-stu-id="3af00-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3af00-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3af00-119">Example</span></span>  
 <span data-ttu-id="3af00-120">O código a seguir mostra um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="3af00-120">The following code shows a complete example.</span></span> <span data-ttu-id="3af00-121">Para saber mais sobre como configurar um projeto que acessa a API do Office, confira [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#](./how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="3af00-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](./how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3af00-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3af00-122">See also</span></span>

- [<span data-ttu-id="3af00-123">Argumentos nomeados e opcionais</span><span class="sxs-lookup"><span data-stu-id="3af00-123">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="3af00-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="3af00-124">dynamic</span></span>](../../language-reference/keywords/dynamic.md)
- [<span data-ttu-id="3af00-125">Usando o tipo dynamic</span><span class="sxs-lookup"><span data-stu-id="3af00-125">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="3af00-126">Como: usar argumentos nomeados e opcionais na programação do Office</span><span class="sxs-lookup"><span data-stu-id="3af00-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="3af00-127">Como: acessar objetos de interoperabilidade do Office usando recursos do Visual C#</span><span class="sxs-lookup"><span data-stu-id="3af00-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="3af00-128">Passo a passo: programação do Office</span><span class="sxs-lookup"><span data-stu-id="3af00-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
