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
ms.openlocfilehash: 81e4047c171e3a58f335821d64390432524b25df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="using-standard-exception-types"></a>Usando tipos de exceção padrão
Esta seção descreve as exceções padrão fornecidas pela estrutura e os detalhes de uso. A lista não é exaustiva. Consulte a documentação de referência do .NET Framework para o uso de outros tipos de exceção do Framework.  
  
## <a name="exception-and-systemexception"></a>Exceção e SystemException  
 **X não** gerar <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X não** catch `System.Exception` ou `System.SystemException` no código do framework, a menos que você pretende relançar.  
  
 **X Evite** capturando `System.Exception` ou `System.SystemException`, exceto em manipuladores de exceção de nível superior.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X não** lançar ou derivam de <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **FAZER ✓** lançar um <xref:System.InvalidOperationException> se o objeto está em um estado inadequado.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException ArgumentNullException e ArgumentOutOfRangeException  
 **FAZER ✓** gerar <xref:System.ArgumentException> ou um de seus subtipos se argumentos inválidos são passados para um membro. Prefira o tipo de exceção mais derivado, se aplicável.  
  
 **FAZER ✓** definir o `ParamName` propriedade ao lançar uma destas subclasses de `ArgumentException`.  
  
 Esta propriedade representa o nome do parâmetro que causou a exceção seja lançada. Observe que a propriedade pode ser definida usando uma das sobrecargas de construtor.  
  
 **FAZER ✓** usar `value` para o nome do parâmetro de valor implícito de setters de propriedade.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException IndexOutOfRangeException e AccessViolationException  
 **X não** permitir que APIs publicamente que pode ser chamado explicitamente ou implicitamente gerar <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, ou <xref:System.IndexOutOfRangeException>. Essas exceções são reservadas e gerada pelo mecanismo de execução e, na que maioria dos casos indicar um bug.  
  
 Fazer a verificação para evitar gerar essas exceções de argumento. Gerar essas exceções expõe detalhes de implementação do seu método que pode ser alterado ao longo do tempo.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X não** lançar explicitamente <xref:System.StackOverflowException>. A exceção deve ser explicitamente lançada apenas pelo CLR.  
  
 **X não** catch `StackOverflowException`.  
  
 É quase impossível escrever código gerenciado que permaneça consistente na presença de estouro de pilha arbitrário. As partes não gerenciadas do CLR permanecem consistentes usando testes para mover o estouro de pilha para locais bem definidos, em vez recuando de estouro de pilha arbitrário.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X não** lançar explicitamente <xref:System.OutOfMemoryException>. Essa exceção é lançada apenas pela infraestrutura do CLR.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException SEHException e ExecutionEngineException  
 **X não** lançar explicitamente <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, e <xref:System.Runtime.InteropServices.SEHException>. Essas exceções devem ser lançada apenas pela infraestrutura do CLR.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)
