---
title: "Documentar seu código com XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML, documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2ec4907ff96a0861f97de21bdf45662c558d0a95
ms.lasthandoff: 03/13/2017

---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Documentando o código com XML (Visual Basic)
Em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], você pode documentar seu código usando XML  
  
## <a name="xml-documentation-comments"></a>Comentários da documentação XML  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fornece uma maneira fácil de automaticamente criar documentação XML para projetos. Você pode gerar automaticamente um esqueleto XML para seus tipos e membros e, em seguida, fornecer resumos, documentação descritiva para cada parâmetro e outros comentários. Com a configuração apropriada, a documentação XML é emitida automaticamente em um arquivo XML com o mesmo nome do projeto e a extensão. XML. Para obter mais informações, consulte [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
 O arquivo XML pode ser consumido ou manipulado como XML. Esse arquivo está localizado no mesmo diretório que o arquivo de saída .exe ou. dll do seu projeto.  
  
 Documentação XML começa com `'''`. O processamento desses comentários tem algumas restrições:  
  
-   A documentação deve ser bem formada XML. Se o XML não está bem formado, um aviso será gerado e o arquivo de documentação contém um comentário dizendo que foi encontrado um erro.  
  
-   Os desenvolvedores são livres para criar seu próprio conjunto de marcas. Há um conjunto recomendado das marcas (consulte "Seções relacionadas" neste tópico). Algumas das marcas recomendadas têm significado especial:  
  
    -   O \<param > marca é usada para descrever os parâmetros. Se usado, o compilador verificará se o parâmetro existe e que todos os parâmetros estão descritos na documentação. Se a verificação falhar, o compilador emite um aviso.  
  
    -   O `cref` atributo pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código. O compilador verifica se este elemento de código existe. Se a verificação falhar, o compilador emite um aviso. O compilador também respeita qualquer `Imports` instruções ao procurar por um tipo descrito o `cref` atributo.  
  
    -   O \<resumo > marca é usada pelo IntelliSense no [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] para exibir informações adicionais sobre um tipo ou membro.  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para obter detalhes sobre como criar um arquivo XML com comentários de documentação, consulte os seguintes tópicos:  
  
-   [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [Processando o Arquivo XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [Como criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Ferramentas XML no Visual Studio](https://docs.microsoft.com/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>Consulte também  
 [Desenvolvendo aplicativos com o Visual Basic](../../../visual-basic/developing-apps/index.md)   
 [Guia de programação em Visual Basic](../../../visual-basic/programming-guide/index.md)
