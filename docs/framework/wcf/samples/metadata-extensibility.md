---
title: Extensibilidade de metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f92fcc76-0806-4c84-9d63-7aae0d3899de
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36eb5940fa1d869948a94fcbbb1945aea1c534ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-extensibility"></a>Extensibilidade de metadados
Esta seção contém exemplos que demonstram metadados personalizados.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Ponto de extremidade de metadados seguros personalizados](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 Demonstra como implementar um serviço com um ponto de extremidade de metadados seguro que usa uma das associações não-metadata exchange e como configurar [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ou clientes para buscar os metadados do tal uma extremidade de metadados.  
  
 [Publicação de WSDL personalizado](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 Demonstra como implementar um <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> em um personalizado <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atributo para exportar as propriedades de atributo como anotações de WSDL, entre outros recursos.
