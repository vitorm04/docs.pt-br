---
title: Exemplo de tabela de UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: 4543d4676344d10c3e380c3522a7ca5a6a8d6294
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59293945"
---
# <a name="uritemplate-table-sample"></a>Exemplo de tabela de UriTemplate
O <xref:System.UriTemplateTable> classe fornece uma estrutura de tabela associativa de dicionário semelhante para trabalhar com um conjunto de `UriTemplate` instâncias. Específico identificadores de recurso uniformes (URIs) possam ser comparados com eficiência com todos os modelos na tabela e dados associados ao modelo correspondente podem ser recuperados.  
  
 Este exemplo demonstra os seguintes conceitos principais relacionados à `UriTemplateTable` classe:  
  
-   Sintaxe para instanciar um `UriTemplateTable`.  
  
-   Populando um `UriTemplateTable` com um conjunto de pares chave/valor.  
  
-   Correspondência de um URI candidato contra a tabela usando <xref:System.UriTemplateTable.MatchSingle%2A>.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a>Consulte também

- [Dispatcher de Tabela de UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
