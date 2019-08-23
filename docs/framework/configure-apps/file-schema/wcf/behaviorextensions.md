---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: bcf1f1dcdba50c3e7fba8eb170132d0cf47c4271
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919816"
---
# <a name="behaviorextensions"></a>\<> behaviorExtensions
As extensões de comportamento permitem que o usuário crie elementos de comportamento definidos pelo usuário. Esses elementos podem ser usados junto com os elementos de comportamento padrão do Windows Communication Foundation (WCF). A `behaviorExtensions` seção define o elemento de modo que ele possa ser usado na configuração. Aqui está um exemplo de uma extensão de comportamento típica.  
  
```xml  
<system.serviceModel>
  <extensions>
    <behaviorExtensions>
      <add name="myBehavior"
           type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </behaviorExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Para adicionar habilidades de configuração ao elemento, você precisa escrever e registrar um elemento de configuração. Para obter mais informações sobre isso, consulte <xref:System.Configuration> a documentação.  
  
 Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada, conforme mostrado no exemplo a seguir.  
  
```xml  
<behaviors>
  <behavior configurationName="testChannelBehavior">
    <myBehavior />
    <channelSecurity cacheCookies="false"
                     detectReplays="false"
                     maxCachedNonces="9"
                     maxClockSkew="00:00:03"
                     maxCookieCachingTime="00:07:24"
                     replayWindow="00:07:22.2190000" />
  </behavior>
</behaviors>
```  
  
## <a name="security"></a>Segurança  
 É altamente recomendável que você use nomes de assembly totalmente qualificados ao registrar tipos nos `machine.config` arquivos e. `app.config` Se o tipo não for definido exclusivamente, o carregador de tipo CLR pesquisará nos seguintes locais na ordem especificada:  
  
 Se o assembly do tipo for conhecido, o carregador pesquisará os locais de redirecionamento do arquivo de configuração, o GAC, o assembly atual usando as informações de configuração e o diretório base do aplicativo. Se o assembly for desconhecido, o carregador pesquisará o assembly atual, mscorlib e o local retornado pelo manipulador `TypeResolve` de eventos. Essa ordem de pesquisa do CLR pode ser modificada com ganchos, como o mecanismo de encaminhamento de tipo e o evento AppDomain. typeresolve.  
  
 Um invasor pode explorar a ordem de pesquisa do CLR e executar código não autorizado. O uso de nomes totalmente qualificados (fortes) identifica exclusivamente um tipo e aumenta ainda mais a segurança do sistema.  
  
 Para obter mais informações, consulte [como o tempo de execução localiza assemblies](https://go.microsoft.com/fwlink/?LinkId=95336) e <xref:System.AppDomain.TypeResolve>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [Configurando e estendendo o tempo de execução com comportamentos](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
