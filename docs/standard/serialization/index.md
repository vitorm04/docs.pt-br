---
title: Serialização-.NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e6db24326c79ab6509b253c45c27f87a2aacd73c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053356"
---
# <a name="serialization-in-net"></a>Serialização no .NET

A serialização é o processo de conversão do estado de um objeto em um formulário que possa ser persistido ou transportado. O complemento de serialização é desserialização, que converte um fluxo em um objeto. Juntos, esses processos permitem que os dados sejam armazenados e transferidos.  
  
O .NET apresenta as seguintes tecnologias de serialização:  
  
- A [serialização binária](binary-serialization.md) preserva a fidelidade do tipo, que é útil para preservar o estado de um objeto entre diferentes invocações de um aplicativo. Por exemplo, você pode compartilhar um objeto entre diferentes aplicativos serializando-o para a área de transferência. Você pode serializar um objeto para um fluxo, um disco, a memória, pela rede, e assim por diante. O acesso remoto usa a serialização para passar objetos “por valor” de um computador ou domínio de aplicativo para outro.  
  
- A [serialização de XML e SOAP](xml-and-soap-serialization.md) serializa apenas campos e propriedades públicas e não preserva a fidelidade do tipo. Isso é útil quando você deseja fornecer ou consumir dados sem restringir o aplicativo que usa os dados. Como o XML é um padrão aberto, é uma opção atrativa para compartilhar dados pela Web. SOAP é, da mesma forma, um padrão aberto, uma opção atrativa.  
  
- A [serialização JSON](system-text-json-overview.md) serializa apenas as propriedades públicas e não preserva a fidelidade do tipo. JSON é um padrão aberto que é uma opção atraente para compartilhar dados na Web.

## <a name="reference"></a>Referência

<xref:System.Runtime.Serialization>  
Contém classes que podem ser usadas para serialização e desserialização de objetos.
  
<xref:System.Xml.Serialization>  
Contém classes que podem ser usadas para serializar objetos em documentos ou fluxos de formato XML.

<xref:System.Text.Json>  
Contém classes que podem ser usadas para serializar objetos em fluxos ou documentos de formato JSON.
