---
title: WebContentTypeMapper Sample
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 540e5e775cf7b2a5a5b585d98772415653fa833a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143558"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper Sample
Esta amostra demonstra como mapear novos tipos de conteúdo para os formatos de corpo de mensagem da Windows Communication Foundation (WCF).  
  
 O <xref:System.ServiceModel.Description.WebHttpEndpoint> elemento conecta-se ao codificador de mensagens da Web, que permite que o WCF receba mensagens binárias JSON, XML ou raw no mesmo ponto final. O codificador determina o formato do corpo da mensagem olhando para o tipo de conteúdo HTTP da solicitação. Esta amostra introduz <xref:System.ServiceModel.Channels.WebContentTypeMapper> a classe, que permite ao usuário controlar o mapeamento entre o tipo de conteúdo e o formato do corpo.  
  
 O WCF fornece um conjunto de mapeamentos padrão para tipos de conteúdo. Por exemplo, `application/json` mapas para `text/xml` JSON e mapas para XML. Qualquer tipo de conteúdo que não seja mapeado para JSON ou XML é mapeado para o formato binário bruto.  
  
 Em alguns cenários (por exemplo, APIs estilo push), o desenvolvedor de serviços não controla o tipo de conteúdo retornado pelo cliente. Por exemplo, os clientes `text/javascript` podem `application/json`retornar JSON como em vez de . Neste caso, o desenvolvedor do serviço deve <xref:System.ServiceModel.Channels.WebContentTypeMapper> fornecer um tipo que deriva para lidar com o determinado tipo de conteúdo corretamente, conforme mostrado no código de amostra a seguir.  
  
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
  
 O tipo deve <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> substituir o método. O método deve `contentType` avaliar o argumento e <xref:System.ServiceModel.Channels.WebContentFormat.Json>retornar <xref:System.ServiceModel.Channels.WebContentFormat.Xml> <xref:System.ServiceModel.Channels.WebContentFormat.Raw>um <xref:System.ServiceModel.Channels.WebContentFormat.Default>dos seguintes valores: , , ou . O <xref:System.ServiceModel.Channels.WebContentFormat.Default> retorno adia os mapeamentos padrão do codificador de mensagens da Web. No código de amostra `text/javascript` anterior, o tipo de conteúdo é mapeado para JSON, e todos os outros mapeamentos permanecem inalterados.  
  
 Para usar `JsonContentTypeMapper` a classe, use o seguinte em sua Web.config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Para verificar a necessidade de usar o JsonContentTypeMapper, remova o atributo contentTypeMapper do arquivo de configuração acima. A página do cliente falha ao `text/javascript` ser carregada ao tentar usar para enviar conteúdo JSON.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Construa a solução WebContentTypeMapperSample.sln conforme descrito na [construção do Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Navegue `http://localhost/ServiceModelSamples/JCTMClientPage.htm` para (não abra JCTMClientPage.htm no navegador de dentro do diretório do projeto).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
