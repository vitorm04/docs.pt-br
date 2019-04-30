---
title: Estendendo o sistema de metadados
ms.date: 03/30/2017
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
ms.openlocfilehash: 7ccef0c2b908a8f78249742decd6c46a862e541e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991296"
---
# <a name="extending-the-metadata-system"></a>Estendendo o sistema de metadados
O sistema de metadados do Windows Communication Foundation (WCF) é um grupo de interfaces e classes que representam os metadados necessários para implementar aplicativos baseados em serviço. Modificar ou estender as classes ou implementar e configurar as interfaces para exportar e importar metadados personalizados como extensões de descrição linguagem WSDL (Web Services) ou asserções de WS-PolicyAttachments personalizadas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Exportando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 Descreve como implementar e usar o <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface para incorporar declarações de política personalizadas em documentos WSDL.  
  
 [Importando metadados personalizados para uma extensão do WCF](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 Descreve como implementar e usar o <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface para ler e responder às declarações de política personalizadas em documentos WSDL.  
  
 [Publicando e recuperando metadados através de uma associação personalizada](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 Descreve como a troca de metadados sobre ligações personalizadas.
