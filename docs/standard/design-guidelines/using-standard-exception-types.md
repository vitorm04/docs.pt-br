---
title: Usando tipos de exceção padrão
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ea4a61be3a76c30c564cbf98ba3318fc6c3e7d4
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46509142"
---
# <a name="using-standard-exception-types"></a>Usando tipos de exceção padrão
Esta seção descreve as exceções padrão fornecidas pela estrutura e os detalhes de uso. A lista não é exaustiva. Consulte a documentação de referência do .NET Framework para o uso de outros tipos de exceção do Framework.  
  
## <a name="exception-and-systemexception"></a>Exceção e SystemException  
 **X DO NOT** gerar <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X DO NOT** catch `System.Exception` ou `System.SystemException` no código do framework, a menos que você pretende relançar.  
  
 **X AVOID** capturando `System.Exception` ou `System.SystemException`, exceto em manipuladores de exceção de nível superior.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** lançar ou derivam de <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** lançar um <xref:System.InvalidOperationException> se o objeto está em um estado inadequado.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException e ArgumentOutOfRangeException  
 **✓ DO** gerar <xref:System.ArgumentException> ou um de seus subtipos se argumentos inválidos são passados para um membro. Prefira o tipo de exceção mais derivado, se aplicável.  
  
 **✓ DO** definir o `ParamName` propriedade ao lançar uma destas subclasses de `ArgumentException`.  
  
 Essa propriedade representa o nome do parâmetro que causou a exceção seja lançada. Observe que a propriedade pode ser definida usando uma das sobrecargas de construtor.  
  
 **✓ DO** usar `value` para o nome do parâmetro de valor implícito de setters de propriedade.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException e AccessViolationException  
 **X DO NOT** permitir que APIs publicamente que pode ser chamado explicitamente ou implicitamente gerar <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, ou <xref:System.IndexOutOfRangeException>. Essas exceções são reservadas e gerada pelo mecanismo de execução e, na que maioria dos casos indicam um bug.  
  
 Fazer a verificação para evitar o lançamento essas exceções de argumento. Gerar essas exceções expõe os detalhes da implementação do método que pode ser alterado ao longo do tempo.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** lançar explicitamente <xref:System.StackOverflowException>. A exceção deve ser explicitamente gerada apenas pelo CLR.  
  
 **X DO NOT** catch `StackOverflowException`.  
  
 É quase impossível escrever código gerenciado que permanece consistente na presença de estouros de pilha arbitrário. As partes não gerenciadas do CLR permaneçam consistentes usando investigações para mover a estouros de pilha para locais bem definidos em vez fazendo-out de estouros de pilha arbitrário.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** lançar explicitamente <xref:System.OutOfMemoryException>. Essa exceção é gerada apenas pela infraestrutura do CLR.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, SEHException e ExecutionEngineException  
 **X DO NOT** lançar explicitamente <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, e <xref:System.Runtime.InteropServices.SEHException>. Essas exceções são seja lançada apenas pela infraestrutura do CLR.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)
