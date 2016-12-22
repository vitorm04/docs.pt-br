---
title: "Estrutura do programa e conven&#231;&#245;es de c&#243;digo (Visual Basic) | Microsoft Docs"
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
  - "convenções de codificação"
  - "Código do Visual Basic, convenções de codificação"
  - "convenções, Visual Basic de codificação"
  - "programas de estrutura"
  - "estrutura do programa"
  - "convenções de nomenclatura, Visual Basic"
  - "práticas recomendadas, convenções de codificação"
  - "convenções de codificação do Visual Basic"
  - "código do Visual Basic"
  - "Programando, convenções de codificação do Visual Basic"
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Estrutura do programa e conven&#231;&#245;es de c&#243;digo (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Esta seção apresenta a estrutura de programa típica do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], fornece um programa simples do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], "Hello, World" e discute as convenções de código do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Convenções de código são sugestões que se centram não em uma lógica do programa mas sobre as estrutura física e aparência.  Se você os seguir, seu código ficará mais fácil de ler, compreender e manter.  Convenções de código podem incluir, entre outros:  
  
-   Formatos padronizados para o código de rotulagem ou de comentários.  
  
-   Diretrizes para espaçamento, formatação e recuo do código.  
  
-   Convenções de nomeação para objetos, variáveis e procedimentos.  
  
 Os tópicos a seguir apresentam um conjunto de diretrizes de programação para programas do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], além de exemplos de bom uso.  
  
## Nesta seção  
 [Estrutura de um programa Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 Fornece uma visão geral dos elementos que compõem um programa em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [Procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 Aborda o procedimento que serve como ponto de partida e controle geral para seu aplicativo.  
  
 [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 Discute como fazer referência a objetos em outros assemblies.  
  
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 Descreve como namespaces organizam objetos em assemblies.  
  
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 Inclui diretrizes gerais para nomear procedimentos, constantes, variáveis, argumentos e objetos.  
  
 [Convenções de codificação do Visual Basic](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 Revisa as diretrizes usadas no desenvolvimento de exemplos nesta documentação.  
  
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Descreve como compilar blocos específicos de código seletivamente e, ao mesmo tempo, direcionar o compilador para ignorar outros.  
  
 [Como quebrar e combinar instruções no código](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)  
 Mostra como dividir instruções longas em várias linhas e combinar instruções curtas em uma linha.  
  
 [Como recolher e ocultar seções do código](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 Mostra como recolher e ocultar seções de código no editor de códigos do [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] .  
  
 [Como rotular instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 Mostra como marcar uma linha de código para identificá\-lo para uso com outras instruções, como `On Error Goto`.  
  
 [Caracteres especiais no código](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 Mostra como e onde usar caracteres não numéricos e não alfabéticos.  
  
 [Comentários no código](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 Discute como adicionar comentários descritivos ao código.  
  
 [Palavras\-chave como nomes de elemento em código](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 Descreve como usar colchetes \(`[]`\) para delimitar os nomes de variáveis que também são palavras\-chave de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 Descreve várias maneiras de fazer referência aos elementos de um programa de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [Limitações do Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 Discute a remoção de limites de codificação conhecidos no [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## Seções relacionadas  
 [Convenções tipográficas e de código](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 Fornece convenções de codificação padrão para o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [Escrevendo código](/visual-studio/ide/writing-code-in-the-code-and-text-editor)  
 Descreve os recursos que tornam mais fácil para você escrever e gerencia seu código.