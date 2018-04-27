---
title: Documentando o código com XML (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 645dd4a8a9d1c78fd54f0f31ad0efd772b671d39
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Documentando o código com XML (Visual Basic)
No Visual Basic, você pode documentar seu código usando XML  
  
## <a name="xml-documentation-comments"></a>Comentários da documentação XML  
 Visual Basic oferece uma maneira fácil para automaticamente criar documentação XML para projetos. Você pode gerar automaticamente um esqueleto XML para seus tipos e membros e, em seguida, fornecer resumos, documentação descritiva para cada parâmetro e outros comentários. Com a configuração apropriada, a documentação XML é emitida automaticamente em um arquivo XML com o mesmo nome do projeto e a extensão. XML. Para obter mais informações, consulte [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
 O arquivo XML pode ser consumido ou manipulado como XML. Esse arquivo está localizado no mesmo diretório que o arquivo de saída .exe ou. dll do projeto.  
  
 Documentação XML começa com `'''`. O processamento desses comentários tem algumas restrições:  
  
-   A documentação deve ser em XML bem formado. Se o XML não está bem formado, um aviso será gerado e o arquivo de documentação contém um comentário dizendo que ocorreu um erro.  
  
-   Os desenvolvedores são livres para criar seu próprio conjunto de marcas. Há um conjunto de marcas (consulte "Seções relacionadas" neste tópico). Algumas das marcas recomendadas têm significado especial:  
  
    -   A marca \<param> é usada para descrever parâmetros. Se ela for usada, o compilador verificará se o parâmetro existe e se todos os parâmetros são descritos na documentação. Se a verificação falhar, o compilador emite um aviso.  
  
    -   O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código. O compilador verifica se este elemento de código existe. Se a verificação falhar, o compilador emite um aviso. O compilador também respeita quaisquer `Imports` instruções ao procurar por um tipo descrito no `cref` atributo.  
  
    -   O \<resumo > marca é usada pelo IntelliSense no [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] para exibir informações adicionais sobre um tipo ou membro.  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para obter detalhes sobre como criar um arquivo XML com comentários de documentação, consulte os tópicos a seguir:  
  
-   [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [Processando o Arquivo XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Ferramentas XML no Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo aplicativos com o Visual Basic](../../../visual-basic/developing-apps/index.md)  
 [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)
