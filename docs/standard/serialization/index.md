---
title: Serialização no .NET
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e05d358452a247b0d071f78d19c0bf721502899a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="serialization-in-net"></a>Serialização no .NET
A serialização é o processo de conversão do estado de um objeto em um formulário que possa ser persistido ou transportado. O complemento de serialização é desserialização, que converte um fluxo em um objeto. Juntos, esses processos permitem que os dados sejam facilmente armazenados e transferidos.  
  
O .NET conta com duas tecnologias de serialização:  
  
-   A serialização binária preserva a fidelidade do tipo, que é útil para preservar o estado de um objeto entre diferentes chamadas de um aplicativo. Por exemplo, você pode compartilhar um objeto entre diferentes aplicativos serializando-o para a área de transferência. Você pode serializar um objeto para um fluxo, um disco, a memória, pela rede, e assim por diante. O acesso remoto usa a serialização para passar objetos “por valor” de um computador ou domínio de aplicativo para outro.  
  
-   A serialização XML serializa somente as propriedades públicas e os campos e não preserva a fidelidade de tipo. Isso é útil quando você deseja fornecer ou consumir dados sem restringir o aplicativo que usa os dados. Como o XML é um padrão aberto, é uma opção atrativa para compartilhar dados pela Web. SOAP é, da mesma forma, um padrão aberto, uma opção atrativa.  
  
## <a name="in-this-section"></a>Nesta seção  
[Tópicos com instruções de serialização](../../../docs/standard/serialization/serialization-how-to-topics.md)  
As listas vinculam tópicos de Como fazer contidas nesta seção.
  
[Serialização binária](../../../docs/standard/serialization/binary-serialization.md)  
Descreve o mecanismo de serialização binária que está incluído com o Common Language Runtime.

[Serialização XML e SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
Descreve o mecanismo de serialização de XML e SOAP que está incluído com o Common Language Runtime.

[Ferramentas de serialização](../../../docs/standard/serialization/serialization-tools.md)  
Essas ferramentas ajudam a desenvolver código de serialização.

[Exemplos de serialização](../../../docs/standard/serialization/serialization-samples.md)  
Os exemplos demonstram como fazer a serialização.

## <a name="reference"></a>Referência
O <xref:System.Runtime.Serialization> contém classes que podem ser usadas para serialização e desserialização de objetos.
  
<xref:System.Xml.Serialization>  
Contém classes que podem ser usadas para serializar objetos em documentos ou fluxos de formato XML.