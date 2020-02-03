---
title: Usar tipos de exceção padrão
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743547"
---
# <a name="using-standard-exception-types"></a>Usar tipos de exceção padrão
Esta seção descreve as exceções padrão fornecidas pela estrutura e os detalhes de seu uso. A lista não é, de maneira alguma, completa. Consulte a documentação de referência do .NET Framework para uso de outros tipos de exceção de estrutura.

## <a name="exception-and-systemexception"></a>Exception e SystemException
 ❌ não lança <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType>.

 ❌ não capturar `System.Exception` ou `System.SystemException` no código do Framework, a menos que você pretenda relançar.

 ❌ evitar a captura de `System.Exception` ou `System.SystemException`, exceto em manipuladores de exceção de nível superior.

## <a name="applicationexception"></a>ApplicationException
 ❌ não são lançadas ou derivam de <xref:System.ApplicationException>.

## <a name="invalidoperationexception"></a>InvalidOperationException
 ✔️ lançar um <xref:System.InvalidOperationException> se o objeto estiver em um estado inadequado.

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException e ArgumentOutOfRangeException
 ✔️ gerar <xref:System.ArgumentException> ou um de seus subtipos se argumentos inválidos forem passados para um membro. Prefira o tipo de exceção mais derivada, se aplicável.

 ✔️ Defina a propriedade `ParamName` ao lançar uma das subclasses de `ArgumentException`.

 Essa propriedade representa o nome do parâmetro que causou a geração da exceção. Observe que a propriedade pode ser definida usando uma das sobrecargas do construtor.

 ✔️ Use `value` para o nome do parâmetro de valor implícito dos setters de propriedade.

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException e AccessViolationException
 ❌ não permitem que APIs que podem ser acessadas publicamente lancem <xref:System.NullReferenceException>, <xref:System.AccessViolationException>ou <xref:System.IndexOutOfRangeException>de forma explícita ou implícita. Essas exceções são reservadas e geradas pelo mecanismo de execução e, na maioria dos casos, indicam um bug.

 Faça a verificação de argumento para evitar lançar essas exceções. Lançar essas exceções expõe os detalhes de implementação do método que pode mudar ao longo do tempo.

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌ não lançam <xref:System.StackOverflowException>explicitamente. A exceção deve ser gerada explicitamente apenas pelo CLR.

 ❌ não capturar `StackOverflowException`.

 É quase impossível escrever código gerenciado que permaneça consistente na presença de estouros de pilha arbitrários. As partes não gerenciadas do CLR permanecem consistentes com o uso de investigações para mover estouros de pilha para locais bem definidos em vez de fazer backup de estouros de pilha arbitrários.

## <a name="outofmemoryexception"></a>{1&gt;OutOfMemoryException&lt;1}
 ❌ não lançam <xref:System.OutOfMemoryException>explicitamente. Essa exceção deve ser lançada apenas pela infraestrutura do CLR.

## <a name="comexception-sehexception-and-executionengineexception"></a>COMException, SEHException e ExecutionEngineException
 ❌ não lançam explicitamente <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>e <xref:System.Runtime.InteropServices.SEHException>. Essas exceções devem ser lançadas apenas pela infraestrutura do CLR.

 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)
