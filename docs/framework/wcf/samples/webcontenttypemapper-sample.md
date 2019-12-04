---
title: WebContentTypeMapper Sample
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: ad10444593c69808b86edd5dfdaf6d2aa86f6b1b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715030"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper Sample
Este exemplo demonstra como mapear novos tipos de conteúdo para Windows Communication Foundation (WCF) formatos de corpo de mensagem.  
  
 O elemento <xref:System.ServiceModel.Description.WebHttpEndpoint> conecta o codificador de mensagem da Web, que permite que o WCF receba mensagens binárias JSON, XML ou RAW no mesmo ponto de extremidade. O codificador determina o formato do corpo da mensagem observando o tipo de conteúdo HTTP da solicitação. Este exemplo apresenta a classe <xref:System.ServiceModel.Channels.WebContentTypeMapper>, que permite ao usuário controlar o mapeamento entre o tipo de conteúdo e o formato do corpo.  
  
 O WCF fornece um conjunto de mapeamentos padrão para tipos de conteúdo. Por exemplo, `application/json` mapeia para JSON e `text/xml` mapeia para XML. Qualquer tipo de conteúdo que não esteja mapeado para JSON ou XML é mapeado para o formato binário bruto.  
  
 Em alguns cenários (por exemplo, APIs de estilo push), o desenvolvedor do serviço não controla o tipo de conteúdo retornado pelo cliente. Por exemplo, os clientes podem retornar JSON como `text/javascript` em vez de `application/json`. Nesse caso, o desenvolvedor do serviço deve fornecer um tipo que deriva de <xref:System.ServiceModel.Channels.WebContentTypeMapper> para tratar o tipo de conteúdo fornecido corretamente, conforme mostrado no código de exemplo a seguir.  
  
```csharp  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 O tipo deve substituir o método <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29>. O método deve avaliar o argumento `contentType` e retornar um dos seguintes valores: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>ou <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Retornar <xref:System.ServiceModel.Channels.WebContentFormat.Default> adia os mapeamentos de codificador de mensagem da Web padrão. No código de exemplo anterior, o tipo de conteúdo `text/javascript` é mapeado para JSON e todos os outros mapeamentos permanecem inalterados.  
  
 Para usar a classe `JsonContentTypeMapper`, use o seguinte em seu Web. config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Para verificar o requisito para usar o JsonContentTypeMapper, remova o atributo contentTypeMapper do arquivo de configuração acima. Falha ao carregar a página do cliente ao tentar usar `text/javascript` para enviar conteúdo JSON.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Crie a solução WebContentTypeMapperSample. sln, conforme descrito em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Navegue até `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (não abra JCTMClientPage. htm no navegador de dentro do diretório do projeto).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
