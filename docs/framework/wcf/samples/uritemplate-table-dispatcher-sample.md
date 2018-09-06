---
title: Exemplos de distribuidor de tabela de UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 4a4f725e88e014da241e1042c27bfee270e13268
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787162"
---
# <a name="uritemplate-table-dispatcher-sample"></a>Exemplos de distribuidor de tabela de UriTemplate
O <xref:System.UriTemplateTable> classe fornece uma estrutura de tabela associativa de dicionário semelhante para trabalhar com um conjunto de <xref:System.UriTemplate> instâncias. Este exemplo demonstra um mecanismo básico de expedição criado usando `UriTemplateTable`, um cenário de uso comum para o `UriTemplateTable` classe.  
  
 Este exemplo demonstra os seguintes conceitos principais para o `UriTemplateTable` classe:  
  
-   Associando delegados com `UriTemplates` em um `UriTemplateTable`.  
  
-   Usando <xref:System.UriTemplateTable.MatchSingle%2A> para obter o delegado do manipulador correto para um URI específico.  
  
-   Invocar o delegado de manipulador para processar a solicitação.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Consulte também  
 [Tabela de UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
