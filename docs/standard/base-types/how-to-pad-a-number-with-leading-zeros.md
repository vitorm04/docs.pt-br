---
title: "Como preencher um número com zeros à esquerda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6266807a01e8119ae1410a1ba09cab55c788b4d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>Como preencher um número com zeros à esquerda
É possível adicionar zeros à esquerda de um inteiro usando a [cadeia de caracteres de formato numérico padrão](../../../docs/standard/base-types/standard-numeric-format-strings.md) “D” com um especificador de precisão. Você pode adicionar zeros à esquerda de inteiros e pontos flutuantes usando uma [cadeia de caracteres de formato numérico personalizado](../../../docs/standard/base-types/custom-numeric-format-strings.md). Este tópico mostra como usar os dois métodos para acrescentar um número com zeros à esquerda.  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Para acrescentar um número inteiro com zeros à esquerda com um comprimento específico  
  
1.  Determine o número mínimo de dígitos que o valor inteiro deve exibir. Inclua os dígitos à esquerda nesse número.  
  
2.  Determine se quer exibir o inteiro como valor decimal ou hexadecimal.  
  
    -   Para exibir o número inteiro como um valor decimal, chame seu `ToString(String)` método e passe a cadeia de caracteres "D*n*" como o valor da `format` parâmetro, onde  *n*  representa o comprimento mínimo da cadeia de caracteres.  
  
    -   Para exibir o número inteiro como um valor hexadecimal, chame seu `ToString(String)` método e passe a cadeia de caracteres "X*n*" como o valor da `format` parâmetro, onde  *n*  representa o comprimento mínimo da cadeia de caracteres.  
  
     Você também pode usar a cadeia de caracteres de formato em um método, como <xref:System.String.Format%2A> ou <xref:System.Console.WriteLine%2A>, que usa [formatação composta](../../../docs/standard/base-types/composite-formatting.md).  
  
 O exemplo a seguir formata diversos valores inteiros com zeros à esquerda para que o comprimento total do número formatado tenha pelo menos oito caracteres.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Para acrescentar um número inteiro com uma determinada quantidade de zeros à esquerda  
  
1.  Determine quantos zeros à esquerda o valor inteiro deve exibir.  
  
2.  Determine se quer exibir o inteiro como valor decimal ou hexadecimal. A formatação como valor decimal requer o uso de um especificador de formato padrão “D”; já a formatação como valor hexadecimal exige que você use o especificador de formato padrão “X”.  
  
3.  Determine o comprimento da cadeia de caracteres numérica não acrescentada. Para isso, chame o método `ToString("D").Length` ou `ToString("X").Length` do valor inteiro.  
  
4.  Adicione quantos dígitos zero à esquerda quer incluir na cadeia de caracteres formatada com comprimento da cadeia de caracteres numérica não acrescentada. Isso define o comprimento total da cadeia de caracteres acrescentada.  
  
5.  Chamar o valor de inteiro `ToString(String)` método e passe a cadeia de caracteres "D*n*" para cadeias de caracteres decimais e "X*n*" para cadeias de caracteres hexadecimais, onde  *n*  representa o comprimento total da cadeia de caracteres preenchido. Você também pode usar o "D*n*" ou "X*n*" formato de cadeia de caracteres em um método que dá suporte à formatação composta.  
  
 O exemplo a seguir acrescenta um valor inteiro com cinco dígitos zero à esquerda.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Para acrescentar um valor numérico com zeros à esquerda com comprimento específico  
  
1.  Determine quantos dígitos a representação da cadeia de caracteres de números deve ter à esquerda dos decimais. Inclua os dígitos zero à esquerda no número total de dígitos.  
  
2.  Defina uma cadeia de caracteres de formato numérico personalizado que usa o espaço reservado com valor zero (“0”) para representar a quantidade mínima de dígitos zero.  
  
3.  Chame o método `ToString(String)` do número e apresente-o à cadeia de caracteres de formato personalizado. Você também pode usar uma cadeia de caracteres de formato personalizado com um método compatível com formatação de composição.  
  
 O exemplo a seguir formata diversos valores numéricos com zeros à esquerda para que o comprimento total do número formatado tenha pelo menos oito caracteres à esquerda do decimal.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Para acrescentar um valor numérico com uma determinada quantidade de zeros à esquerda  
  
1.  Determine quantos zeros à esquerda o valor numérico deve ter.  
  
2.  Determine a quantidade de dígitos à esquerda do decimal na cadeia de caracteres numéricos não acrescentada. Para fazer isso:  
  
    1.  Determine se a representação da cadeia de caracteres de um número inclui um símbolo de ponto decimal.  
  
    2.  Caso o símbolo esteja presente, determine a quantidade de caracteres à esquerda do ponto decimal.  
  
         - ou -  
  
         Caso o símbolo não esteja presente, determine o comprimento da cadeia de caracteres.  
  
3.  Crie uma cadeia de caracteres de formato personalizado que use o espaço reservado zero ("0") para que cada um dos dígitos zero à esquerda apareça na cadeia de caracteres e que use o espaço reservado zero ou de dígito ("#") para representar cada dígito na cadeia de caracteres padrão.  
  
4.  Forneça a cadeia de caracteres de formato personalizado como parâmetro para o método `ToString(String)` do número ou para um método que use a formatação composta.  
  
 O exemplo a seguir acrescenta dois valores <xref:System.Double> com cinco dígitos zero à esquerda.  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Cadeias de caracteres de formato numérico personalizado](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Cadeias de Caracteres de Formato Numérico Padrão](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [Formatação de composição](../../../docs/standard/base-types/composite-formatting.md)
