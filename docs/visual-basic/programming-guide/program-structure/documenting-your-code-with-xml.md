---
title: "Documentando o c&#243;digo com XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "código do Visual Basic, documentação com XML"
  - "comentários XML, Visual Basic"
  - "XML, código de documentação"
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Documentando o c&#243;digo com XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], você pode documentar seu código usando XML  
  
## Comentários da Documentação XML  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece uma maneira fácil de automaticamente criar documentação XML para projetos.  Você pode gerar automaticamente um esqueleto XML para tipos e membros e, em seguida, fornecer resumos, documentação descritiva para cada parâmetro e outros comentários.  Com a instalação apropriada, a documentação XML é emitida automaticamente em um arquivo XML com o mesmo nome do projeto e a extensão .xml.  Para obter mais informações, consulte [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
 O arquivo XML pode ser consumido ou manipulado como XML.  Este arquivo está localizado no mesmo diretório que o arquivo de saída .exe ou .dll do projeto.  
  
 A documentação XML começa com `'''`.  O processamento desses comentários tem algumas restrições:  
  
-   A documentação deve ser XML bem formado.  Se o XML não for bem formado, um aviso é gerado e o arquivo de documentação conterá um comentário informando que foi encontrado um erro.  
  
-   Os desenvolvedores estão livres para criar seu próprio conjunto de marcas.  Há um conjunto recomendado das marcas \(consulte "Seções Relacionadas" neste tópico\).  Algumas das marcas recomendadas têm significado especial:  
  
    -   A marca \<param\> é usada para descrever os parâmetros.  Se usado, o compilador verificará se o parâmetro existe e que todos os parâmetros estão descritos na documentação.  Se a verificação falhar, o compilador emite um aviso.  
  
    -   O atributo `cref` pode ser anexado a qualquer marca para fornecer uma referência a um elemento de código.  O compilador verifica se este elemento de código existe.  Se a verificação falhar, o compilador emite um aviso.  O compilador também respeita quaisquer instruções `Imports` ao procurar por um tipo descrito no atributo `cref`.  
  
    -   A marca \<resumo\> é usada pelo IntelliSense no [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] para exibir informações adicionais sobre um tipo ou membro.  
  
## Seções relacionadas  
 Para obter detalhes sobre a criação de um arquivo XML com comentários de documentação, consulte os seguintes tópicos:  
  
-   [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [Processando o arquivo XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [Como criar documentação XML](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)  
  
-   [Ferramentas XML no \(Visual Studio\)](/visual-studio/xml-tools/xml-tools-in-visual-studio)  
  
## Consulte também  
 [Desenvolvendo aplicativos com o Visual Basic](../../../visual-basic/developing-apps/index.md)   
 [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)