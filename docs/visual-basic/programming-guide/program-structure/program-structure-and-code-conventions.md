---
title: "Estrutura do programa e convenções de código (Visual Basic) | Documentos do Microsoft"
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
- coding conventions
- Visual Basic code, coding conventions
- coding conventions, Visual Basic
- programs, structure
- program structure
- naming conventions, Visual Basic
- best practices, coding conventions
- conventions, Visual Basic coding
- Visual Basic code
- programming, Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
caps.latest.revision: 21
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cd25d99d74bf1e4d416c9da63758f6ad04027258
ms.lasthandoff: 03/13/2017

---
# <a name="program-structure-and-code-conventions-visual-basic"></a>Estrutura do programa e convenções de código (Visual Basic)
Esta seção apresenta o típico [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] estrutura do programa, fornece uma simples [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de programa "Hello, World" e discute [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convenções de código. Convenções de código são sugestões que o foco não na lógica do programa, mas em sua estrutura física e aparência. Depois delas torna seu código mais fácil de ler, compreender e manter. Convenções de código podem incluir, entre outros:  
  
-   Formatos padronizados para rotular e comentando o código.  
  
-   Diretrizes para espaçamento, formatação e recuo do código.  
  
-   Convenções de nomenclatura para objetos, variáveis e procedimentos.  
  
 Os tópicos a seguir apresentam um conjunto de diretrizes para de programação [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programas, junto com exemplos de uso de BOM.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estrutura de um programa Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 Fornece uma visão geral dos elementos que compõem um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.  
  
 [Procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 Descreve o procedimento que serve como o início do ponto e controle geral para seu aplicativo.  
  
 [Referências e a Instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 Discute como fazer referência a objetos em outros assemblies.  
  
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 Descreve como namespaces organizam objetos em assemblies.  
  
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 Inclui diretrizes gerais para nomear procedimentos, constantes, variáveis, argumentos e objetos.  
  
 [Convenções de codificação do Visual Basic](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 Revisa as diretrizes usadas no desenvolvimento de exemplos nesta documentação.  
  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Descreve como compilar específicos blocos de código seletivamente ao direcionar o compilador ignorar outros.  
  
 [Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 Mostra como dividir instruções longas em várias linhas e combinar instruções curtas em uma linha.  
  
 [Como recolher e ocultar seções do código](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 Mostra como recolher e ocultar seções de código de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] editor de códigos.  
  
 [Como rotular instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 Mostra como marcar uma linha de código para identificá-lo para uso com instruções de como `On Error Goto`.  
  
 [Caracteres Especiais no Código](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 Mostra como e onde usar caracteres não alfabéticos e não-numéricos.  
  
 [Comentários no Código](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 Descreve como adicionar comentários descritivos ao seu código.  
  
 [Palavras-chave como Nomes de Elemento em Código](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 Descreve como usar colchetes (`[]`) para delimitar nomes de variáveis que são também [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] palavras-chave.  
  
 [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 Descreve várias maneiras de se referir a elementos de um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa.  
  
 [Limitações do Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 Discute a remoção dos limites de codificação conhecidos em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Convenções Tipográficas e de Código](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 Fornece as convenções de codificação padrão para [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 [Escrevendo código](https://docs.microsoft.com/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 Descreve os recursos que tornam mais fácil para escrever e gerenciar seu código.
