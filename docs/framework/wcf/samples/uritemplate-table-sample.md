---
title: Exemplo de tabela de UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: c0aed1a49faf74ab9fd463769aab66ad72e74038
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183258"
---
# <a name="uritemplate-table-sample"></a>Exemplo de tabela de UriTemplate
A <xref:System.UriTemplateTable> classe fornece uma estrutura de tabela associativa `UriTemplate` semelhante a um dicionário para trabalhar com um conjunto de instâncias. Os URIs (Uniform Resource Identifiers, identificadores uniformes específicos) podem ser combinados eficientemente com todos os modelos da tabela, e os dados associados ao modelo combinado podem ser recuperados.  
  
 Esta amostra demonstra os seguintes `UriTemplateTable` conceitos-chave relacionados à classe:  
  
- Sintaxe para instanciar um `UriTemplateTable`.  
  
- Povoando `UriTemplateTable` um com um conjunto de pares de chave/valor.  
  
- Combinando um URI candidato <xref:System.UriTemplateTable.MatchSingle%2A>contra a tabela usando .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a>Confira também

- [Dispatcher de Tabela de UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [Uritemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
