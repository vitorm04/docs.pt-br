---
title: "Fun&#231;&#245;es da cadeia de caracteres (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "funções de cadeia de caracteres"
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fun&#231;&#245;es da cadeia de caracteres (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A tabela a seguir lista as funções que o Visual Basic oferece para pesquisar e manipular cadeias de caracteres.  
  
|Método .NET Framework|Descrição|  
|---------------------------|---------------|  
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|Retorna um valor `Integer` que representa o código de caractere correspondente a um caractere.|  
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|Retorna o caractere associado ao código de caractere especificado.|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|Retorna uma matriz baseada em zero que contém um subconjunto de uma matriz `String` com base em critérios de filtragem especificados.|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|Retorna uma cadeia de caracteres formatada de acordo com as instruções contidas em uma expressão de formato `String`.|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|Retorna uma expressão formatada como um valor de moeda usando o símbolo de moeda definido no painel de controle do sistema.|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|Retorna uma expressão de cadeia de caracteres que representa um valor de data\/hora.|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|Retorna uma expressão formatada como um número.|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|Retorna uma expressão formatada como uma porcentagem \(isto é, multiplicado por 100\) com um % à direita de caracteres.|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|Retorna um inteiro especificando a posição de início da primeira ocorrência de uma cadeia de caracteres dentro da outra.|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|Retorna a posição da primeira ocorrência de uma cadeia de caracteres em outra, começando do lado direito da cadeia de caracteres.|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|Retorna uma cadeia de caracteres criada juntando um certo número de subcadeias de caracteres contidas em uma matriz.|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|Retorna uma cadeia de caracteres ou um caractere convertido em minúsculas.|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|Retorna uma cadeia de caracteres contendo um número especificado de caracteres do lado esquerdo de uma cadeia de caracteres.|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|Retorna um inteiro que contém o número de caracteres em uma cadeia de caracteres.|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|Retorna uma cadeia de caracteres alinhada à esquerda que contêm a cadeia de caracteres especificada ajustada ao comprimento especificado.|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|Retorna uma cadeia de caracteres que contém uma cópia de uma cadeia de caracteres especificada sem espaços iniciais.|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|Retorna uma cadeia de caracteres contendo um número especificado de caracteres de uma cadeia de caracteres.|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|Retorna uma cadeia de caracteres na qual uma subcadeia de caracteres especificada foi substituída por outra subcadeia de caracteres um determinado número de vezes.|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|Retorna uma cadeia de caracteres contendo um número especificado de caracteres do lado direito de uma cadeia de caracteres.|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|Retorna uma cadeia de caracteres alinhada à direita que contêm a cadeia de caracteres especificada ajustada ao comprimento especificado.|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|Retorna uma cadeia de caracteres que contém uma cópia de uma cadeia de caracteres especificada sem espaços finais.|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|Retorna uma cadeia de caracteres consistindo em um número de espaços especificado.|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|Retorna uma matriz unidimensional baseada em zero contendo um número especificado de subcadeias.|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|Retorna \-1, 0, ou 1, com base no resultado de uma comparação de cadeia de caracteres.|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|Retorna uma cadeia de caracteres convertida como especificado.|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|Retorna uma cadeia de caracteres ou o objeto que consiste no caractere especificado repetido o número de vezes especificado.|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|Retorna uma cadeia de caracteres em que a ordem de caracteres de uma cadeia de caracteres especificada é invertida.|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|Retorna uma cadeia de caracteres que contém uma cópia de uma cadeia de caracteres especificada sem espaços inicial ou final.|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|Retorna uma cadeia de caracteres ou um caractere com a cadeia de caracteres especificada convertida para maiúsculas.|  
  
 É possível usar a declaração [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) para definir se as cadeias de caracteres são comparadas usando um ordem de classificação sem diferenciação de maiúsculas e minúsculas de texto determinada pela localização do sistema \(`Text`\) ou pelas representações binárias internas dos caracteres \(`Binary`\).  O método de comparação de texto padrão é `Binary`.  
  
## Exemplo  
 Este exemplo usa a função `UCase` para retornar uma versão de uma cadeia de caracteres em letras minúsculas.  
  
 [!code-vb[VbVbalrStrings#31](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_1.vb)]  
  
## Exemplo  
 Este exemplo usa a função `LTrim` para retirar espaços à esquerda e a função `RTrim` para retirar espaços à direita de um variável de cadeia de caracteres.  Usa a função de `Trim` para retirar ambos os tipos de espaços.  
  
 [!code-vb[VbVbalrStrings#25](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_2.vb)]  
  
## Exemplo  
 Este exemplo usa a função `Mid` para retornar um número especificado de caracteres de uma cadeia de caracteres.  
  
 [!code-vb[VbVbalrStrings#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_3.vb)]  
  
## Exemplo  
 Este exemplo usa `Len` para retornar o número especificado de caracteres em uma cadeia de caracteres.  
  
 [!code-vb[VbVbalrStrings#33](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_4.vb)]  
  
## Exemplo  
 Este exemplo usa a função `InStr` para retornar a posição da primeira ocorrência de uma cadeia de caracteres dentro da outra.  
  
 [!code-vb[VbVbalrStrings#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_5.vb)]  
  
## Exemplo  
 Este exemplo mostra vários usos da função `Format` para formatar valores usando os formatos `String` e os formatos definidos pelo usuário.  Para o separador de data \(`/`\), separador de hora \(`:`\) e indicadores AM\/PM \(`t` e `tt`\), a saída formatada real exibida pelo seu sistema depende das configurações de localidade que o código está usando.  Quando horas e datas são exibidas no ambiente de desenvolvimento, o formato abreviado de tempo e o formato abreviado de data do local do código são usados.  
  
> [!NOTE]
>  Para localidades que usam um relógio de 24 horas, os indicadores AM\/PM \(`t` e `tt`\) não exibem nada.  
  
 [!code-vb[VbVbalrStrings#27](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_6.vb)]  
  
## Consulte também  
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Membros da biblioteca em tempo de execução do Visual Basic](../../../visual-basic/language-reference/runtime-library-members.md)   
 [Resumo de manipulação da cadeia de caracteres](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)