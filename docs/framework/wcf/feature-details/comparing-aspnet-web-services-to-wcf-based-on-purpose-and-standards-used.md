---
title: Comparando serviços Web do ASP.NET ao WCF com base na finalidade e nos padrões usados
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: 74ef2f3f3505125f8720695e218617817fcae82d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548372"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>Comparando serviços Web do ASP.NET ao WCF com base na finalidade e nos padrões usados
Serviços Web do ASP.NET foi desenvolvido para a criação de aplicativos que enviam e recebem mensagens usando o SOAP Simple Object Access Protocol () em HTTP. A estrutura das mensagens pode ser definida usando um esquema XML, e uma ferramenta é fornecida para facilitar a serializar as mensagens para e de objetos do .NET Framework. A tecnologia pode gerar automaticamente os metadados para descrever serviços Web na descrição de linguagem WSDL (Web Services) e uma segunda ferramenta é fornecida para a geração de clientes para serviços Web do WSDL.  
  
 O WCF é para habilitar aplicativos do .NET Framework trocar mensagens com outras entidades de software. SOAP é usado por padrão, mas as mensagens podem estar em qualquer formato e transmitidas por meio de qualquer protocolo de transporte. A estrutura das mensagens pode ser definida usando um esquema XML, e há várias opções para serializar as mensagens para e de objetos do .NET Framework. O WCF pode gerar automaticamente os metadados para descrever aplicativos criados usando a tecnologia em WSDL, e também fornece uma ferramenta para gerar clientes para os aplicativos a partir de WSDL.  
  
 Os padrões com suporte pelos serviços da Web do ASP.NET estão documentados em [XML Web Services criados usando ASP.NET](https://go.microsoft.com/fwlink/?LinkId=94872). A lista mais abrangente de padrões com suporte do WCF são listados em [Web Services protocolos com suporte pelas associações de interoperabilidade System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## <a name="see-also"></a>Consulte também
- [Comparando serviços Web do ASP.NET ao WCF com base em desenvolvimento](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
