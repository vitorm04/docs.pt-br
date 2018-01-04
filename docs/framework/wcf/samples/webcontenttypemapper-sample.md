---
title: WebContentTypeMapper Sample
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34adf191d3edbff33fe989cf036c32104a6754ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper Sample
Este exemplo demonstra como mapear os novos tipos de conteúdo para [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] formatos de corpo de mensagem.  
  
 O <xref:System.ServiceModel.Description.WebHttpEndpoint> elemento se conecta o codificador de mensagem da Web, que permite [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para receber mensagens de binárias brutas no mesmo ponto de extremidade, XML ou JSON. O codificador determina o formato do corpo da mensagem, observando o tipo de conteúdo HTTP da solicitação. Este exemplo apresenta o <xref:System.ServiceModel.Channels.WebContentTypeMapper> classe, que permite ao usuário controlar o mapeamento entre o tipo de conteúdo e o formato do corpo.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um conjunto de mapeamentos padrão para tipos de conteúdo. Por exemplo, `application/json` mapeia para JSON e `text/xml` mapeia para XML. Qualquer tipo de conteúdo que não está mapeado para JSON ou XML é mapeado para o formato binário bruto.  
  
 Em alguns cenários (por exemplo, APIs push-style), o desenvolvedor de serviço não controla o tipo de conteúdo retornado pelo cliente. Por exemplo, os clientes podem retornar JSON como `text/javascript` em vez de `application/json`. Nesse caso, o desenvolvedor de serviço deve fornecer um tipo que deriva de <xref:System.ServiceModel.Channels.WebContentTypeMapper> para lidar com o tipo de conteúdo fornecido corretamente, conforme mostrado no código de exemplo a seguir.  
  
```  
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
  
 O tipo deve substituir o <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> método. O método deve avaliar o `contentType` argumento e retornar um dos seguintes valores: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, ou <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Retornando <xref:System.ServiceModel.Channels.WebContentFormat.Default> transfere para os mapeamentos de codificador de mensagem de Web padrão. No código de exemplo anterior, o `text/javascript` conteúdo tipo é mapeado para JSON, e todos os outros mapeamentos permanecem inalterados.  
  
 Para usar o `JsonContentTypeMapper` de classe, use o seguinte no Web. config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Para verificar se o requisito para usar o JsonContentTypeMapper, remova o atributo de contentTypeMapper do arquivo de configuração acima. A página do cliente não for carregado durante a tentativa de usar `text/javascript` para enviar conteúdo o JSON.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução WebContentTypeMapperSample.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Navegue até http://localhost/ServiceModelSamples/JCTMClientPage.htm (não abrir JCTMClientPage.htm no navegador de dentro do diretório do projeto).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a>Consulte também
