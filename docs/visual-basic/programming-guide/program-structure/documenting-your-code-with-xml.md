---
title: Documentando o código com XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 6b9fe9994b7bdf2259dcdb1ecef906e0f9955c8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785496"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="27a9d-102">Documentando o código com XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27a9d-102">Documenting Your Code with XML (Visual Basic)</span></span>

<span data-ttu-id="27a9d-103">No Visual Basic, você pode documentar seu código usando XML</span><span class="sxs-lookup"><span data-stu-id="27a9d-103">In Visual Basic, you can document your code using XML</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="27a9d-104">Comentários da documentação XML</span><span class="sxs-lookup"><span data-stu-id="27a9d-104">XML Documentation Comments</span></span>

<span data-ttu-id="27a9d-105">Visual Basic fornece uma maneira fácil de criar automaticamente a documentação XML para projetos.</span><span class="sxs-lookup"><span data-stu-id="27a9d-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="27a9d-106">Você pode gerar automaticamente um esqueleto XML para seus tipos e membros e, em seguida, fornecer resumos, documentação descritiva para cada parâmetro e outros comentários.</span><span class="sxs-lookup"><span data-stu-id="27a9d-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="27a9d-107">Com a configuração apropriada, a documentação XML é emitida automaticamente em um arquivo XML com o mesmo nome do projeto e a extensão. XML.</span><span class="sxs-lookup"><span data-stu-id="27a9d-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="27a9d-108">Para obter mais informações, consulte [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="27a9d-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="27a9d-109">O arquivo XML pode ser consumido ou manipulado como XML.</span><span class="sxs-lookup"><span data-stu-id="27a9d-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="27a9d-110">Esse arquivo está localizado no mesmo diretório que o arquivo de saída .exe ou. dll do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="27a9d-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="27a9d-111">Documentação XML começa com `'''`.</span><span class="sxs-lookup"><span data-stu-id="27a9d-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="27a9d-112">O processamento desses comentários tem algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="27a9d-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="27a9d-113">A documentação deve ser em XML bem formado.</span><span class="sxs-lookup"><span data-stu-id="27a9d-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="27a9d-114">Se o XML não está bem formado, um aviso será gerado e o arquivo de documentação contém um comentário dizendo que foi encontrado um erro.</span><span class="sxs-lookup"><span data-stu-id="27a9d-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="27a9d-115">Os desenvolvedores são livres para criar seu próprio conjunto de marcas.</span><span class="sxs-lookup"><span data-stu-id="27a9d-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="27a9d-116">Há um conjunto recomendado de marcas (consulte "Seções relacionadas" neste tópico).</span><span class="sxs-lookup"><span data-stu-id="27a9d-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="27a9d-117">Algumas das marcas recomendadas têm significado especial:</span><span class="sxs-lookup"><span data-stu-id="27a9d-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="27a9d-118">A marca \<param> é usada para descrever parâmetros.</span><span class="sxs-lookup"><span data-stu-id="27a9d-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="27a9d-119">Se ela for usada, o compilador verificará se o parâmetro existe e se todos os parâmetros são descritos na documentação.</span><span class="sxs-lookup"><span data-stu-id="27a9d-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="27a9d-120">Se a verificação falhar, o compilador emite um aviso.</span><span class="sxs-lookup"><span data-stu-id="27a9d-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="27a9d-121">O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código.</span><span class="sxs-lookup"><span data-stu-id="27a9d-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="27a9d-122">O compilador verifica se esse elemento de código existe.</span><span class="sxs-lookup"><span data-stu-id="27a9d-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="27a9d-123">Se a verificação falhar, o compilador emite um aviso.</span><span class="sxs-lookup"><span data-stu-id="27a9d-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="27a9d-124">O compilador também respeita qualquer `Imports` instruções ao procurar por um tipo descrito o `cref` atributo.</span><span class="sxs-lookup"><span data-stu-id="27a9d-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="27a9d-125">O \<resumo > marca é usada pelo IntelliSense no Visual Studio para exibir informações adicionais sobre um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="27a9d-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="27a9d-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="27a9d-126">Related Sections</span></span>

<span data-ttu-id="27a9d-127">Para obter detalhes sobre como criar um arquivo XML com comentários de documentação, consulte os tópicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="27a9d-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="27a9d-128">/doc</span><span class="sxs-lookup"><span data-stu-id="27a9d-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)

- [<span data-ttu-id="27a9d-129">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="27a9d-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

- [<span data-ttu-id="27a9d-130">Processando o Arquivo XML</span><span class="sxs-lookup"><span data-stu-id="27a9d-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [<span data-ttu-id="27a9d-131">Como: Criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="27a9d-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [<span data-ttu-id="27a9d-132">Ferramentas XML no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="27a9d-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="27a9d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27a9d-133">See also</span></span>

- [<span data-ttu-id="27a9d-134">Desenvolvendo aplicativos com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27a9d-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)
- [<span data-ttu-id="27a9d-135">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27a9d-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
