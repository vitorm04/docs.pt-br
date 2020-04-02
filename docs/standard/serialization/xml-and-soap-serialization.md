---
title: Serialização XML e SOAP
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: dcb2ed1703473be582a12f430d2e051d8a420230
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588372"
---
# <a name="xml-and-soap-serialization"></a>Serialização de XML e SOAP

A serialização XML converte (serializa) os campos e propriedades públicas de um objeto, e os parâmetros e valores de retorno dos métodos, em um fluxo XML que está em conformidade com um documento específico de linguagem de definição xml schema (XSD). A serialização XML resulta em classes fortemente tipadas com propriedades e campos públicos que são convertidos em um formato serial (neste caso, em XML) para armazenamento ou transporte.

Como XML é um padrão aberto, o fluxo XML pode ser processado por qualquer aplicativo, quando necessário, independentemente da plataforma. Por exemplo, serviços Web XML criados com ASP.NET usam a classe <xref:System.Xml.Serialization.XmlSerializer> para criar fluxos XML que passam dados entre aplicativos de serviço Web XML por toda a Internet ou entre intranets. Por outro lado, a desserialização obtém esse fluxo XML e reconstrói o objeto.

A serialização XML também pode ser usada para serializar objetos em fluxos XML que atendam à especificação SOAP. SOAP é um protocolo baseado em XML, projetado especificamente para transportar chamadas de procedimentos usando XML.

Para serializar e desserializar objetos, use a classe <xref:System.Xml.Serialization.XmlSerializer>. Para criar as classes a serem serializadas, use a ferramenta de definição de esquema XML.

## <a name="see-also"></a>Confira também

- [Serialização binária](binary-serialization.md)
- [XML Web Services criado usando clientes ASP.NET e XML Web Service](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))
