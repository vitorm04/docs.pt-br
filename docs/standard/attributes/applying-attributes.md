---
title: Aplicando atributos
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
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e23649c5d833bef8b74ec5d3b9c22235756580e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="applying-attributes"></a>Aplicando atributos
Use o processo a seguir para aplicar um atributo a um elemento do seu código.  
  
1.  Definir um novo atributo ou use um atributo existente importando seu namespace do .NET Framework.  
  
2.  Aplique o atributo para o elemento de código, colocando-o imediatamente antes do elemento.  
  
     Cada linguagem tem sua própria sintaxe de atributo. Em C++ e c#, o atributo é circundado por colchetes e separado do elemento por espaço em branco, que pode incluir uma quebra de linha. No Visual Basic, o atributo é delimitado por colchetes angulares e deve estar na mesma linha lógica; o caractere de continuação de linha pode ser usado se uma quebra de linha é desejada.
  
3.  Especifique parâmetros posicionais e parâmetros nomeados para o atributo.  
  
     Parâmetros posicionais são necessários e devem vir antes de quaisquer parâmetros nomeados; eles correspondem aos parâmetros de um dos construtores do atributo. Parâmetros nomeados são opcionais e correspondem às propriedades do atributo de leitura/gravação. Em C++ e c#, especifique `name` = `value` para cada parâmetro opcional, onde `name` é o nome da propriedade. No Visual Basic, especifique `name`: =`value`.  
  
 O atributo é emitido em metadados quando você compila o código e está disponível para o common language runtime e qualquer ferramenta personalizada ou um aplicativo por meio dos serviços de reflexão em tempo de execução.  
  
 Por convenção, todos os nomes de atributo terminam com atributo. No entanto, várias linguagens que direcionam o tempo de execução, como Visual Basic e c#, não exigem que você especifique o nome completo de um atributo. Por exemplo, se você deseja inicializar <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, você só precisa fazer referência a ele como **obsoleto**.  
  
## <a name="applying-an-attribute-to-a-method"></a>Aplicar um atributo a um método  
 O exemplo de código a seguir mostra como declarar **System. ObsoleteAttribute**, que as marcas de código como obsoleto. A cadeia de caracteres `"Will be removed in next version"` é passado para o atributo. Esse atributo faz com que um aviso do compilador que exibe a cadeia de caracteres transmitida ao código que descreve o atributo é chamado.  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a>Aplicando atributos no nível de Assembly  
 Se você quiser aplicar um atributo no nível de assembly, use o **assembly** (`Assembly` no Visual Basic) palavra-chave. O código a seguir mostra o **AssemblyTitleAttribute** aplicada no nível de assembly.  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 Quando esse atributo é aplicado, a cadeia de caracteres `"My Assembly"` é colocado no manifesto do assembly na parte de metadados do arquivo. Você pode exibir o atributo usando o [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ou criando um programa personalizado para recuperar o atributo.  
  
## <a name="see-also"></a>Consulte também  
 [Atributos](../../../docs/standard/attributes/index.md)  
 [Recuperando informações armazenadas em atributos](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)  
 [Conceitos](/cpp/windows/attributed-programming-concepts)  
 [Atributos](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
