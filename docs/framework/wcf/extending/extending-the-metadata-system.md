---
title: Estendendo o sistema de metadados
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: d3ce7e1a228e6303be1009c7b72f4e889b40c536
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795727"
---
# <a name="extending-the-metadata-system"></a>Estendendo o sistema de metadados
O sistema de metadados do Windows Communication Foundation (WCF) é um grupo de classes e interfaces que representam os metadados necessários para implementar aplicativos baseados em serviço. Modifique ou estenda as classes ou implemente e configure as interfaces para exportar e importar metadados personalizados, como as extensões WSDL (Web Services Description Language) ou as asserções WS-PolicyAttachments personalizadas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Exportando metadados personalizados para uma extensão do WCF](exporting-custom-metadata-for-a-wcf-extension.md)  
 Descreve como implementar e usar a <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface para inserir declarações de política personalizada em documentos WSDL.  
  
 [Importando metadados personalizados para uma extensão do WCF](importing-custom-metadata-for-a-wcf-extension.md)  
 Descreve como implementar e usar a <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface para ler e responder a declarações de política personalizadas em documentos WSDL.  
  
 [Publicando e recuperando metadados através de uma associação personalizada](publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 Descreve como trocar metadados em associações personalizadas.
