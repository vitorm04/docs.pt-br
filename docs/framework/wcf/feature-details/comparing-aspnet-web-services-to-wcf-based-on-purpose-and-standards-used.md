---
title: Comparando serviços Web do ASP.NET ao WCF com base na finalidade e nos padrões usados
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: 1600a398ac250f015f2a1d9aa4ae2d808c593b95
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963561"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>Comparando serviços Web do ASP.NET ao WCF com base na finalidade e nos padrões usados
Os serviços Web do ASP.NET foram desenvolvidos para criar aplicativos que enviam e recebem mensagens usando o protocolo SOAP por HTTP. A estrutura das mensagens pode ser definida usando um esquema XML, e uma ferramenta é fornecida para facilitar a serialização das mensagens de e para os objetos .NET Framework. A tecnologia pode gerar metadados automaticamente para descrever os serviços Web no WSDL (Web Services Description Language) e uma segunda ferramenta é fornecida para gerar clientes para serviços Web a partir do WSDL.  
  
 O WCF é para permitir que os aplicativos de .NET Framework troquem mensagens com outras entidades de software. O SOAP é usado por padrão, mas as mensagens podem estar em qualquer formato e transmitidas usando qualquer protocolo de transporte. A estrutura das mensagens pode ser definida usando um esquema XML e há várias opções para serializar as mensagens de e para objetos .NET Framework. O WCF pode gerar metadados automaticamente para descrever os aplicativos criados usando a tecnologia em WSDL e também fornece uma ferramenta para gerar clientes para esses aplicativos a partir do WSDL.  
  
 Os padrões com suporte do ASP.NET Web Services são documentados em [benefícios de Web Services XML criados usando o ASP.net](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0859ebft(v=vs.100)). A lista mais abrangente de padrões com suporte pelo WCF é listada em [protocolos de serviços da Web com suporte de associações de interoperabilidade fornecidas pelo sistema](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## <a name="see-also"></a>Veja também

- [Comparando serviços Web do ASP.NET ao WCF com base em desenvolvimento](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
