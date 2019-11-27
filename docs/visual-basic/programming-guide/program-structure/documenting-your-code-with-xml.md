---
title: Documentar o código com XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: bdf0da7a8acc919e4a1d66b81e30c9ed912dd321
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347449"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="9c9fd-102">Documentando o código com XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c9fd-102">Documenting Your Code with XML (Visual Basic)</span></span>

<span data-ttu-id="9c9fd-103">No Visual Basic, você pode documentar seu código usando XML</span><span class="sxs-lookup"><span data-stu-id="9c9fd-103">In Visual Basic, you can document your code using XML</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="9c9fd-104">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="9c9fd-104">XML Documentation Comments</span></span>

<span data-ttu-id="9c9fd-105">Visual Basic fornece uma maneira fácil de criar automaticamente a documentação XML para projetos.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="9c9fd-106">Você pode gerar automaticamente um esqueleto XML para seus tipos e membros e, em seguida, fornecer resumos, documentação descritiva para cada parâmetro e outros comentários.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="9c9fd-107">Com a configuração apropriada, a documentação XML é emitida automaticamente em um arquivo XML com o mesmo nome que o seu projeto e a extensão. xml.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="9c9fd-108">Para obter mais informações, confira [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="9c9fd-108">For more information, see [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="9c9fd-109">O arquivo XML pode ser consumido ou manipulado de outra forma como XML.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="9c9fd-110">Esse arquivo está localizado no mesmo diretório que o arquivo. exe ou. dll de saída do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="9c9fd-111">A documentação XML começa com `'''`.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="9c9fd-112">O processamento desses comentários tem algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="9c9fd-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="9c9fd-113">A documentação deve ser em XML bem formado.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="9c9fd-114">Se o XML não estiver bem formado, um aviso será gerado e o arquivo de documentação conterá um comentário dizendo que foi encontrado um erro.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="9c9fd-115">Os desenvolvedores são livres para criar seu próprio conjunto de marcas.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="9c9fd-116">Há um conjunto recomendado de marcas (consulte "seções relacionadas" neste tópico).</span><span class="sxs-lookup"><span data-stu-id="9c9fd-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="9c9fd-117">Algumas das marcas recomendadas têm significado especial:</span><span class="sxs-lookup"><span data-stu-id="9c9fd-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="9c9fd-118">A marca \<param> é usada para descrever parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="9c9fd-119">Se ela for usada, o compilador verificará se o parâmetro existe e se todos os parâmetros são descritos na documentação.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="9c9fd-120">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="9c9fd-121">O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="9c9fd-122">O compilador verifica se esse elemento de código existe.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="9c9fd-123">Se a verificação falhar, o compilador emitirá um aviso.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="9c9fd-124">O compilador também respeita quaisquer instruções `Imports` ao procurar um tipo descrito no atributo `cref`.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="9c9fd-125">A marca de > de Resumo de \<é usada pelo IntelliSense no Visual Studio para exibir informações adicionais sobre um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="9c9fd-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="9c9fd-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="9c9fd-126">Related Sections</span></span>

<span data-ttu-id="9c9fd-127">Para obter detalhes sobre como criar um arquivo XML com comentários de documentação, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="9c9fd-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="9c9fd-128">-doc</span><span class="sxs-lookup"><span data-stu-id="9c9fd-128">-doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)

- [<span data-ttu-id="9c9fd-129">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="9c9fd-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

- [<span data-ttu-id="9c9fd-130">Processando o Arquivo XML</span><span class="sxs-lookup"><span data-stu-id="9c9fd-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [<span data-ttu-id="9c9fd-131">Como criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="9c9fd-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [<span data-ttu-id="9c9fd-132">Ferramentas XML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9c9fd-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="9c9fd-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c9fd-133">See also</span></span>

- [<span data-ttu-id="9c9fd-134">Desenvolvendo aplicativos com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c9fd-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)
- [<span data-ttu-id="9c9fd-135">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c9fd-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
