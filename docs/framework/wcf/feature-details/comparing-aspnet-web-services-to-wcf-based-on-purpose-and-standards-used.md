---
title: Comparando serviços Web do ASP.NET ao WCF com base na finalidade e nos padrões usados
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: 60f2e9ccbfd5dbf205f3ed570ece1d4169f21e3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>Comparando serviços Web do ASP.NET ao WCF com base na finalidade e nos padrões usados
Serviços Web do ASP.NET foi desenvolvido para criar aplicativos que enviem e recebam mensagens usando o protocolo de acesso de objeto simples (SOAP) por HTTP. A estrutura das mensagens de erro pode ser definida usando um esquema XML, e uma ferramenta é fornecida para facilitar a serializar as mensagens para e de objetos do .NET Framework. A tecnologia pode gerar automaticamente os metadados para descrever serviços Web no WSDL Web Services Description Language () e uma segunda ferramenta é fornecida para a geração de clientes para serviços Web do WSDL.  
  
 O WCF é para habilitar aplicativos do .NET Framework trocar mensagens com outras entidades de software. SOAP é usado por padrão, mas as mensagens podem estar em qualquer formato e transmitidas usando qualquer protocolo de transporte. A estrutura das mensagens de erro pode ser definida usando um esquema XML, e há várias opções para serializar as mensagens para e de objetos do .NET Framework. WCF pode gerar automaticamente os metadados para descrever os aplicativos criados usando a tecnologia em WSDL, e também fornece uma ferramenta para gerar os clientes para os aplicativos de WSDL.  
  
 Os padrões de serviços da Web ASP.NET com suporte estão documentados em [XML Web Services criado usando ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872). A lista mais ampla de padrões com suporte do WCF são listados em [Web Services dá suporte para protocolos associações de interoperabilidade System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## <a name="see-also"></a>Consulte também  
 [Comparando serviços Web do ASP.NET ao WCF com base em desenvolvimento](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
