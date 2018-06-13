---
title: '&lt;behaviorExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: bb59ceeb478d0324fddc98a206a00dbd170b5ac9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749576"
---
# <a name="ltbehaviorextensionsgt"></a>&lt;behaviorExtensions&gt;
Extensões de comportamento permitem ao usuário criar elementos de comportamento definidos pelo usuário. Esses elementos podem ser usados junto com os elementos de comportamento padrão do Windows Communication Foundation (WCF). O `behaviorExtensions` seção define o elemento de modo que ele pode ser usado na configuração. Aqui está um exemplo de uma extensão de comportamento típico.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="myBehavior" type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
       </behaviorExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Para adicionar recursos de configuração para o elemento, você precisa escrever e registrar um elemento de configuração. Para obter mais informações sobre isso, consulte o <xref:System.Configuration> documentação.  
  
 Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada, conforme mostrado no exemplo a seguir.  
  
```xml  
<behaviors>  
    <behavior configurationName="testChannelBehavior">  
        <myBehavior />  
        <channelSecurity cacheCookies="false" detectReplays="false" maxCachedNonces="9"  
            maxClockSkew="00:00:03" maxCookieCachingTime="00:07:24" replayWindow="00:07:22.2190000" />  
    </behavior>  
</behaviors>  
```  
  
## <a name="security"></a>Segurança  
 É altamente recomendável que você use nomes de assembly totalmente qualificado ao registrar tipos no `machine.config` e `app.config` arquivos. Se o tipo não é exclusivamente definido, o carregador de tipo CLR pesquisa nos seguintes locais na ordem especificada:  
  
 Se o assembly do tipo for conhecido, o carregador de pesquisa locais de redirecionamento do arquivo de configuração, GAC, o assembly atual usando as informações de configuração e o diretório base do aplicativo. Se o assembly for desconhecido, o carregador de pesquisa do assembly atual, mscorlib e o local retornado pelo `TypeResolve` manipulador de eventos. Essa ordem de pesquisa do CLR pode ser modificada com ganchos de como o mecanismo de encaminhamento de tipo e o evento AppDomain.TypeResolve.  
  
 Um invasor pode explorar a ordem de pesquisa CLR e executar código não autorizado. Usando os nomes totalmente qualificados (fortes) exclusivamente identifica um tipo e aumenta ainda mais a segurança do sistema.  
  
 Para obter mais informações, consulte [como o tempo de execução Localiza Assemblies](http://go.microsoft.com/fwlink/?LinkId=95336) e <xref:System.AppDomain.TypeResolve>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
 [Configurando e estendendo o tempo de execução com comportamentos](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
