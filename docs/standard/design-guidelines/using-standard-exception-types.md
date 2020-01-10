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
ms.openlocfilehash: 6b202d618d9d2216c8998181303250081de6781c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708978"
---
# <a name="using-standard-exception-types"></a>Usar tipos de exceção padrão
Esta seção descreve as exceções padrão fornecidas pela estrutura e os detalhes de seu uso. A lista não é, de maneira alguma, completa. Consulte a documentação de referência do .NET Framework para uso de outros tipos de exceção de estrutura.  
  
## <a name="exception-and-systemexception"></a>Exception e SystemException  
 **X DO NOT** gerar <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X DO NOT** catch `System.Exception` ou `System.SystemException` no código do framework, a menos que você pretende relançar.  
  
 **X AVOID** capturando `System.Exception` ou `System.SystemException`, exceto em manipuladores de exceção de nível superior.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** lançar ou derivam de <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** lançar um <xref:System.InvalidOperationException> se o objeto está em um estado inadequado.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException e ArgumentOutOfRangeException  
 **✓ DO** gerar <xref:System.ArgumentException> ou um de seus subtipos se argumentos inválidos são passados para um membro. Prefira o tipo de exceção mais derivada, se aplicável.  
  
 **✓ DO** definir o `ParamName` propriedade ao lançar uma destas subclasses de `ArgumentException`.  
  
 Essa propriedade representa o nome do parâmetro que causou a geração da exceção. Observe que a propriedade pode ser definida usando uma das sobrecargas do construtor.  
  
 **✓ DO** usar `value` para o nome do parâmetro de valor implícito de setters de propriedade.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException e AccessViolationException  
 **X DO NOT** permitir que APIs publicamente que pode ser chamado explicitamente ou implicitamente gerar <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, ou <xref:System.IndexOutOfRangeException>. Essas exceções são reservadas e geradas pelo mecanismo de execução e, na maioria dos casos, indicam um bug.  
  
 Faça a verificação de argumento para evitar lançar essas exceções. Lançar essas exceções expõe os detalhes de implementação do método que pode mudar ao longo do tempo.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** lançar explicitamente <xref:System.StackOverflowException>. A exceção deve ser gerada explicitamente apenas pelo CLR.  
  
 **X DO NOT** catch `StackOverflowException`.  
  
 É quase impossível escrever código gerenciado que permaneça consistente na presença de estouros de pilha arbitrários. As partes não gerenciadas do CLR permanecem consistentes com o uso de investigações para mover estouros de pilha para locais bem definidos em vez de fazer backup de estouros de pilha arbitrários.  
  
## <a name="outofmemoryexception"></a>{1&gt;OutOfMemoryException&lt;1}  
 **X DO NOT** lançar explicitamente <xref:System.OutOfMemoryException>. Essa exceção deve ser lançada apenas pela infraestrutura do CLR.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>COMException, SEHException e ExecutionEngineException  
 **X DO NOT** lançar explicitamente <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, e <xref:System.Runtime.InteropServices.SEHException>. Essas exceções devem ser lançadas apenas pela infraestrutura do CLR.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)
