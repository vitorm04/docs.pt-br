---
title: "Tipos de dados num&#233;ricos (Visual Basic) | Microsoft Docs"
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
  - "tipos de dados [Visual Basic], numérico"
  - "tipo de dados Decimal, tipos de dados numéricos"
  - "tipo de dados Double, tipos de dados numéricos"
  - "expoente, de números fracionários"
  - "tipos de dados fracionários"
  - "frações"
  - "tipo de dados Integer, tipos de dados numéricos"
  - "números inteiros"
  - "números inteiros"
  - "tipos integrais, Visual Basic"
  - "tipo de dados Long, tipos de dados numéricos do Visual Basic"
  - "mantissas"
  - "mantissas, de números fracionários"
  - "números"
  - "números, inteiro"
  - "números, inteiro"
  - "tipos de dados numéricos, Visual Basic"
  - "tipo de dados Short, tipos de dados numéricos"
  - "tipo de dados Single, tipos numéricos"
  - "números inteiros"
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados num&#233;ricos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece vários  *tipos de dados numéricos*  para tratar números em diversas representações.  Tipos *Integral* representam apenas números inteiros \(positivo, negativo e zero\), e tipos *nonintegral* representam números com partes inteira e fracionária.  
  
 Para obter uma tabela que mostre uma comparação lado\-a\-lado dos [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados, consulte [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## Tipos Numéricos Integral  
 *Tipos de dados integral*  são aqueles que representam apenas números sem partes fracionárias.  
  
 Os tipos de dados integral *com sinal* são [Tipo de dados SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) \(8\-bit\), [Tipo de dados curto](../../../../visual-basic/language-reference/data-types/short-data-type.md) \(16 bits\), [Tipo de dados inteiro](../../../../visual-basic/language-reference/data-types/integer-data-type.md) \(32 bits\) e [Tipo de dados Long](../../../../visual-basic/language-reference/data-types/long-data-type.md) \(64 bits\).  Se uma variável sempre armazena números inteiros em vez de números fracionários, declare\-a como um desses tipos.  
  
 O tipos integral *sem sinal* são [Tipo de dados Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md) \(8\-bit\), [Tipo de dados UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) \(16 bits\), [Tipo de dados UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) \(32 bits\) e [Tipo de dados ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) \(64 bits\).  Se uma variável contiver dados binários, ou de natureza desconhecida, declare\-a como um desses tipos.  
  
### Desempenho  
 Operações aritméticas são mais rápidas com tipos integrais do que com outros tipos de dados.  Eles são mais rápidos com tipos `Integer` e `UInteger` no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### Inteiros Grandes  
 Se você precisar armazenar um número inteiro maior que o `Integer` pode conter o tipo de dados, você pode usar o `Long` em vez disso, o tipo de dados.  `Long`variáveis podem armazenar números de \-9.223.372.036.854.775.808 através de 9.223.372.036.854.775.807.  Operações com `Long` são um pouco mais lento do que com `Integer`.  
  
 Se você precisar de valores ainda maiores, você pode usar o [Tipo de dados decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md).  Você pode armazenar números de\-79,228,162,514,264,337,593,543,950,335 até 79,228,162,514,264,337,593,543,950,335 em uma variável `Decimal` se você não usa nenhuma casa decimal.  No entanto, operações com números `Decimal` números são consideravelmente mais lentas do que com qualquer outro tipo de dados numérico.  
  
### Inteiros Pequenos  
 Se você não precisar toda a gama da `Integer` tipo de dados, você pode usar o `Short` tipo de dados que pode conter números inteiros de \-32.768 até 32.767.  Para o menor intervalo inteiro, o `SByte` tipo de dados contém inteiros de \-128 a 127.  Se você tiver um grande número de variáveis que armazenar números inteiros pequenos, o common language runtime, às vezes, pode armazenar seu `Short` e `SByte` variáveis de maneira mais eficiente e economizar o consumo de memória.  No entanto, operações com `Short` e `SByte` são um pouco mais lentas do que com `Integer`.  
  
### Integers Sem Sinal  
 Se você souber que sua variável nunca precisará armazenar um número negativo, você pode usar os *tipos sem sinal*  `Byte`,`UShort`,`UInteger` e `ULong`.  Cada um desses tipos de dados pode conter um número inteiro positivo duas vezes o tamanho de seu tipo com sinal correspondente \(`SByte`,`Short`,`Integer` e `Long`\).  Em termos de desempenho, cada tipo sem sinal é tão eficiente quanto seu tipo com sinal correspondente.  Em particular, `UInteger` compartilha com `Integer` a distinção de ser o mais eficiente de todos os tipos de dados numérico elementar.  
  
## Tipos Numéricos Nonintegral  
 *Os tipos de dados nonintegral*  são aqueles que representam números com partes inteira e fracionária.  
  
 Os tipos de dados numéricos nonintegral são `Decimal` \(128 bits fixo ponto\), [Tipo de dados único](../../../../visual-basic/language-reference/data-types/single-data-type.md) \(32\-bit ponto flutuante\) e [Tipo de dados double](../../../../visual-basic/language-reference/data-types/double-data-type.md) \(64\-Bit ponto flutuante\).  Todos eles são tipos com sinal.  Se uma variável pode conter uma fração, declare\-a como um desses tipos.  
  
 `Decimal`não é um tipo de dados de ponto flutuante.  `Decimal`números têm um valor inteiro binário e um fator de escala de número inteiro que especifica qual parte do valor é uma fração decimal.  
  
 Você pode usar `Decimal` variáveis para valores de dinheiro.  A vantagem é a precisão dos valores.  O tipo de dados `Double` é mais rápido e requer menos memória, mas é requerente to erros de arredondamento.  O `Decimal` tipo de dados mantém total precisão para 28 casas decimais.  
  
 Números ponto flutuante \(`Single` e `Double`\) têm Intervalos maiores do que números `Decimal` mas podem ser sujeitos a erros de arredondamento.  Tipos de ponto flutuante suportam menos dígitos significativos que `Decimal` mas podem representar valores de magnitude maior.  
  
 Valores numéricos Nonintegral podem ser expressos como mmmEeee, em que mmm é a *mantissa* \(os dígitos significativos\) e eee é o *expoente* \(uma potência de 10\).  Os valores positivos mais altos dos tipos nonintegral são 7.9228162514264337593543950335E \+ 28 para `Decimal`, 3.4028235E \+ 38 para `Single` e 1.79769313486231570E \+ 308 para `Double`.  
  
### Desempenho  
 `Double` é o  mais eficiente dos tipos de dados fracionários, porque os processadores em plataformas atuais executam operações de ponto flutuante com precisão dupla.  No entanto, operações com `Double` não são tão rápidas como com os tipos integrais como `Integer`.  
  
### Magnitudes Pequenas  
 Para números com o menor magnitude possível \(próximos a 0\), variáveis `Double` podem conter números tão pequenos quanto \- 4.94065645841246544E\- 324  para valores negativos e 4.94065645841246544E \- 324 para valores positivos.  
  
### Números Fracionários Pequenos  
 Se você não precisar toda a gama da `Double` tipo de dados, você pode usar o `Single` tipo de dados que pode conter números de ponto flutuante de \- 3.4028235E \+ 38 a 3.4028235E \+ 38.  As magnitudes menores para `Single` as variáveis são \- 1, 401298E\-45 para valores negativos e 1, 401298E\-45 para valores positivos.  Se você tiver um grande número de variáveis que armazenam números de ponto flutuante pequenos, o Common Language Runtime pode, às vezes, armazenar as variáveis `Single` forma mais eficiente e economizar memória.  
  
## Consulte também  
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados de caractere](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [Tipos de dados diversos](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Como chamar uma função do Windows que use tipos não assinados](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)