---
title: "Como exportar metadados para pontos de extremidade de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d076878f31d162713feaecc0a92c2f6f534897b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-export-metadata-from-service-endpoints"></a>Como exportar metadados para pontos de extremidade de serviço
Este tópico explica como exportar metadados de pontos de extremidade de serviço.  
  
### <a name="to-export-metadata-from-service-endpoints"></a>Para exportar metadados de pontos de extremidade de serviço  
  
1.  Crie um projeto de aplicativo de Console novo de Visual Studio. Adicione o código mostrado nas etapas a seguir no arquivo Program.cs gerado no método Main ().  
  
2.  Criará um <xref:System.ServiceModel.Description.WsdlExporter>.  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  Definir o <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> um dos valores de propriedade a <xref:System.ServiceModel.Description.PolicyVersion> enumeração. Este exemplo define o valor como <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> que corresponde ao WS-Policy 1.5.  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4.  Crie uma matriz de <xref:System.ServiceModel.Description.ServiceEndpoint> objetos.  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5.  Exportação de metadados para cada ponto de extremidade de serviço.  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6.  Verifique para certificar-se de que nenhum erro ocorreu durante o processo de exportação e recuperar os metadados.  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7.  Agora você pode usar os metadados, como gravá-la em um arquivo chamando o <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> método.  
  
## <a name="example"></a>Exemplo  
 A seguir está a listagem completa de códigos deste exemplo.  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Ao compilar referência Program.cs System.ServiceModel.dll.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da arquitetura de metadados](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [Uso de metadados](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [Pontos de extremidade: Endereços, associações e contratos](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
