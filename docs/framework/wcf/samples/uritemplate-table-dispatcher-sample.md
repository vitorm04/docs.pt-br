---
title: Exemplos de distribuidor de tabela de UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: aa4259f8c823bebf38b9689df92c45992cb55723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143675"
---
# <a name="uritemplate-table-dispatcher-sample"></a>Exemplos de distribuidor de tabela de UriTemplate
A <xref:System.UriTemplateTable> classe fornece uma estrutura de tabela associativa <xref:System.UriTemplate> semelhante a um dicionário para trabalhar com um conjunto de instâncias. Esta amostra demonstra um mecanismo `UriTemplateTable`de despacho básico construído `UriTemplateTable` usando , um cenário de uso comum para a classe.  
  
 Esta amostra demonstra os seguintes conceitos-chave para a `UriTemplateTable` classe:  
  
- Associando delegados `UriTemplates` em `UriTemplateTable`um .  
  
- Usando <xref:System.UriTemplateTable.MatchSingle%2A> para obter o delegado manipulador correto para um URI específico.  
  
- Invocando o delegado manipulador para processar a solicitação.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>Confira também

- [Tabela de UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [Uritemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
