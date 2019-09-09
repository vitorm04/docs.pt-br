---
title: Dicas de desempenho do .NET
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0c4177faca86fab9934f1cae57f02f8e42a2ae0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943372"
---
# <a name="net-performance-tips"></a>Dicas de desempenho do .NET
O termo *desempenho* geralmente se refere à velocidade de execução de um programa. Às vezes, você pode aumentar a velocidade de execução seguindo algumas regras básicas em seu código-fonte. Em alguns programas, é importante examinar atentamente o código e usar criadores de perfil para verificar se eles estão executando o mais rápido possível. Em outros programas, você não precisa executar essa otimização porque o código é executado em velocidade aceitável conforme ele é gravado. Este artigo lista algumas áreas comuns em que o desempenho pode ser prejudicado e dicas para melhorá-lo, bem como links para tópicos adicionais sobre desempenho. Para obter mais informações sobre como planejar e medir o desempenho, consulte [Desempenho](../../../docs/framework/performance/index.md)  
  
## <a name="boxing-and-unboxing"></a>Conversão boxing e unboxing  
 É melhor evitar o uso de tipos de valor em situações em que eles devem sofrer conversão boxing um grande número de vezes, por exemplo, em classes de coleções não genéricas como <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Você pode evitar a conversão boxing de tipos de valor por meio de coleções genéricas como <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. As conversões boxing e unboxing são processos computacionalmente dispendiosos. Quando um tipo de valor é convertido, um objeto totalmente novo deve ser criado. Isso pode levar até 20 vezes mais tempo que a atribuição de uma referência simples. Ao fazer unboxing, o processo de conversão pode demorar quatro vezes mais que uma atribuição. Para obter mais informações, consulte [Boxing e unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Cadeias de caracteres  
 Ao concatenar um grande número de variáveis de cadeia de caracteres, por exemplo em um loop estreito, use <xref:System.Text.StringBuilder?displayProperty=nameWithType> em vez do [operador +](../../csharp/language-reference/operators/addition-operator.md) de C# ou dos [operadores de concatenação](../../visual-basic/language-reference/operators/concatenation-operators.md) do Visual Basic. Para obter mais informações, confira [Como: Concatenar várias cadeias de caracteres](../../csharp/how-to/concatenate-multiple-strings.md) e [operadores de concatenação no Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Destruidores  
 Destruidores vazios não devem ser usados. Quando uma classe contém um destruidor, uma entrada é criada na fila Finalizar. Quando o destruidor é chamado, o coletor de lixo é invocado para processar a fila. Se o destruidor estiver vazio, isso apenas resultará em uma perda de desempenho. Para obter mais informações, consulte [destruidores](../../csharp/programming-guide/classes-and-structs/destructors.md) e tempo de [vida do objeto: Como os objetos são criados e](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)destruídos.  
  
## <a name="other-resources"></a>Outros recursos  
  
- [Escrevendo código gerenciado mais rápido: Saiba o que as coisas custam](https://go.microsoft.com/fwlink/?LinkId=99294)  
  
- [Escrevendo aplicativos gerenciados de alto desempenho: Um primer](https://go.microsoft.com/fwlink/?LinkId=99295)  
  
- [Noções básicas do coletor de lixo e dicas de desempenho](https://go.microsoft.com/fwlink/?LinkId=99296)  
  
- [Dicas e truques sobre desempenho em aplicativos .NET](https://go.microsoft.com/fwlink/?LinkId=99297)  

- [Informações úteis sobre desempenho, por Rico Mariani](https://go.microsoft.com/fwlink/?LinkId=115679)  

- [Blog de Vance Morrison](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a>Consulte também

- [Desempenho](../../../docs/framework/performance/index.md)
- [Guia de programação do Visual Basic](../../visual-basic/programming-guide/index.md)
- [Guia de Programação em C#](../../csharp/programming-guide/index.md)
