---
title: WebContentTypeMapper Sample
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 91e5cca478521a343f7528f878f114b85eff2d08
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674187"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper Sample
Este exemplo demonstra como mapear os novos tipos de conteúdo para formatos de corpo de mensagem do Windows Communication Foundation (WCF).  
  
 O <xref:System.ServiceModel.Description.WebHttpEndpoint> conecta-o elemento no codificador de mensagem da Web, que permite ao WCF receber mensagens de binárias brutas no mesmo ponto de extremidade, XML ou JSON. O codificador determina o formato do corpo da mensagem, observando o tipo de conteúdo HTTP da solicitação. Esta amostra apresenta o <xref:System.ServiceModel.Channels.WebContentTypeMapper> classe, que permite ao usuário controlar o mapeamento entre o tipo de conteúdo e o formato do corpo.  
  
 O WCF fornece um conjunto de mapeamentos padrão para tipos de conteúdo. Por exemplo, `application/json` é mapeado para JSON e `text/xml` mapeia para XML. Qualquer tipo de conteúdo que não está mapeado para JSON ou XML é mapeado para o formato binário bruto.  
  
 Em alguns cenários (por exemplo, APIs de estilo push), o desenvolvedor de serviço não controla o tipo de conteúdo retornado pelo cliente. Por exemplo, os clientes podem retornar JSON como `text/javascript` em vez de `application/json`. Nesse caso, o desenvolvedor de serviço deve fornecer um tipo que deriva de <xref:System.ServiceModel.Channels.WebContentTypeMapper> para lidar com o tipo de conteúdo fornecido corretamente, conforme mostrado no código de exemplo a seguir.  
  
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
  
 O tipo deve substituir o <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> método. O método deve ser avaliada a `contentType` argumento e retornam uma dos seguintes valores: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, ou <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Retornando <xref:System.ServiceModel.Channels.WebContentFormat.Default> adiado para os mapeamentos de codificador de mensagem de Web padrão. No código de exemplo anterior, o `text/javascript` conteúdo tipo é mapeado para JSON, e todos os outros mapeamentos permanecem inalterados.  
  
 Para usar o `JsonContentTypeMapper` de classe, use o seguinte no seu Web. config:  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Para verificar se o requisito para usar o JsonContentTypeMapper, remova o atributo contentTypeMapper do arquivo de configuração acima. A página do cliente não carrega ao tentar usar `text/javascript` enviar JSON conteúdo.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução WebContentTypeMapperSample.sln, conforme descrito em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Navegue até http://localhost/ServiceModelSamples/JCTMClientPage.htm (não abrir JCTMClientPage.htm no navegador de dentro do diretório do projeto).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a>Consulte também
