---
title: Como exibir milissegundos em valores de data e hora
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
- DateTime.ToString method
- displaying date and time data
- time [.NET Framework], milliseconds
- dates [.NET Framework], milliseconds
- milliseconds [.NET Framework]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 260d202eb0a218a6657bc719e36da6f39138e54e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a>Como exibir milissegundos em valores de data e hora
A data padrão e a hora formatação métodos, como <xref:System.DateTime.ToString?displayProperty=nameWithType>, incluem horas, minutos e segundos de um valor de tempo, mas exclui seu componente de milissegundos. Este tópico mostra como incluir um componente de milissegundos de uma data e hora em cadeias de caracteres de data e hora formatadas.  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a>Para exibir o componente de milissegundos de um valor DateTime  
  
1.  Se você estiver trabalhando na representação da cadeia de caracteres de uma data, converta-a para um valor <xref:System.DateTime> ou <xref:System.DateTimeOffset> usando a estatística <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> ou o método <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType>.  
  
2.  Para extrair a representação de cadeia de caracteres do componente tempo de milissegundo, chame a data e hora do valor <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.ToString%2A> método e passar o `fff` ou `FFF` padrões de formato personalizado sozinho ou com outro formato personalizado especificadores de como o `format` parâmetro.  
  
## <a name="example"></a>Exemplo  
 O exemplo exibe o componente de milissegundo de um <xref:System.DateTime> e um <xref:System.DateTimeOffset> valor no console sozinho e incluído em uma cadeia de caracteres de data e hora mais.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 O padrão de formato `fff` inclui os zeros à direita no valor de milissegundos. O padrão de formato `FFF` os suprime. A diferença é ilustrada no exemplo a seguir.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 Um problema ao definir um especificador de formato personalizado completo que inclui o componente de milissegundos de uma data e hora é que ele define um formato embutido em código que pode não corresponder à organização de elementos de hora na cultura atual do aplicativo. É uma alternativa melhor recuperar uma data e hora padrões de exibição definidos a cultura atual <xref:System.Globalization.DateTimeFormatInfo> de objeto e modificá-lo para incluir milissegundos. O exemplo também ilustra esta abordagem. Recupera a cultura atual total padrão de data e hora do <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> propriedade e, em seguida, insere o padrão personalizado `.ffff` após seu padrão de segundos. Observe que o exemplo usa uma expressão regular para executar esta operação em uma única chamada de método.  
  
 Você também pode usar um especificador de formato personalizado para exibir uma parte fracionária dos segundos que não sejam milissegundos. Por exemplo, o especificador de formato personalizado `f` ou `F` exibe décimos de segundo, o especificador de formato personalizado `ff` ou `FF` exibe centésimos de segundo e o especificador de formato personalizado `ffff` ou `FFFF` exibe décimos de milésimos de segundo. Partes fracionárias de um milissegundo são truncadas em vez de arredondadas na cadeia de caracteres retornada. Esses especificadores de formato são usados no exemplo a seguir.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  É possível exibir unidades fracionárias muito pequenas de um segundo, como dez milésimos de segundo ou centésimos de milésimos de segundo. No entanto, esses valores podem não ser significativos. A precisão dos valores de data e hora depende da resolução do relação ao relógio do sistema. No Windows NT 3.5 e versões posteriores, e [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] sistemas operacionais, a resolução do relógio é aproximadamente 10 a 15 milissegundos.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Compile o código na linha de comando com csc.exe ou vb.exe. Para compilar o código em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], coloque-o em um modelo de projeto de aplicativo de console.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [Cadeias de caracteres de formato de data e hora personalizado](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
