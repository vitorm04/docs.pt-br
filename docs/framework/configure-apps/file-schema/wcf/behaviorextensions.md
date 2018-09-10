---
title: '&lt;behaviorExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: d025497956715913923e839cb6c482f44f96babb
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44196888"
---
# <a name="ltbehaviorextensionsgt"></a>&lt;behaviorExtensions&gt;
Extensões de comportamento permitem ao usuário criar elementos de comportamento definidos pelo usuário. Esses elementos podem ser usados juntamente com os elementos de comportamento padrão do Windows Communication Foundation (WCF). O `behaviorExtensions` seção define o elemento, de modo que ele pode ser usado na configuração. Aqui está um exemplo de uma extensão de comportamento típico.  
  
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
  
 Para adicionar capacidades de configuração para o elemento, você precisa escrever e registrar um elemento de configuração. Para obter mais informações sobre isso, consulte o <xref:System.Configuration> documentação.  
  
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
 É altamente recomendável que você use nomes de assembly totalmente qualificados ao registrar tipos na `machine.config` e `app.config` arquivos. Se o tipo não é exclusivamente definido, o carregador do tipo CLR procura-lo nos seguintes locais na ordem especificada:  
  
 Se o assembly do tipo for conhecido, o carregador pesquisará os locais de redirecionamento do arquivo de configuração, GAC, o assembly atual usando as informações de configuração e o diretório base do aplicativo. Se o assembly for desconhecido, o carregador pesquisará o assembly atual, mscorlib e o local retornado pelo `TypeResolve` manipulador de eventos. Essa ordem de pesquisa do CLR pode ser modificada com ganchos, como o mecanismo de encaminhamento de tipo e o evento AppDomain. typeresolve.  
  
 Um invasor pode explorar a ordem de pesquisa do CLR e executar código não autorizado. Usar os nomes totalmente qualificados (fortes) exclusivamente identifica um tipo e aumenta ainda mais a segurança do sistema.  
  
 Para obter mais informações, consulte [como o tempo de execução Localiza Assemblies](https://go.microsoft.com/fwlink/?LinkId=95336) e <xref:System.AppDomain.TypeResolve>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
 [Configurando e estendendo o tempo de execução com comportamentos](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
