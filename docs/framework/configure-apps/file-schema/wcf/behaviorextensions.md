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
# <a name="behaviorextensions"></a><span data-ttu-id="d832d-101">\<> behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="d832d-101">\<behaviorExtensions></span></span>
<span data-ttu-id="d832d-102">As extensões de comportamento permitem que o usuário crie elementos de comportamento definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="d832d-102">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="d832d-103">Esses elementos podem ser usados junto com os elementos de comportamento padrão do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d832d-103">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="d832d-104">A `behaviorExtensions` seção define o elemento de modo que ele possa ser usado na configuração.</span><span class="sxs-lookup"><span data-stu-id="d832d-104">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="d832d-105">Aqui está um exemplo de uma extensão de comportamento típica.</span><span class="sxs-lookup"><span data-stu-id="d832d-105">Here is an example of a typical behavior extension.</span></span>  
  
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
  
 <span data-ttu-id="d832d-106">Para adicionar habilidades de configuração ao elemento, você precisa escrever e registrar um elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="d832d-106">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="d832d-107">Para obter mais informações sobre isso, consulte <xref:System.Configuration> a documentação.</span><span class="sxs-lookup"><span data-stu-id="d832d-107">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="d832d-108">Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d832d-108">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
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
  
## <a name="security"></a><span data-ttu-id="d832d-109">Segurança</span><span class="sxs-lookup"><span data-stu-id="d832d-109">Security</span></span>  
 <span data-ttu-id="d832d-110">É altamente recomendável que você use nomes de assembly totalmente qualificados ao registrar tipos nos `machine.config` arquivos e. `app.config`</span><span class="sxs-lookup"><span data-stu-id="d832d-110">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="d832d-111">Se o tipo não for definido exclusivamente, o carregador de tipo CLR pesquisará nos seguintes locais na ordem especificada:</span><span class="sxs-lookup"><span data-stu-id="d832d-111">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="d832d-112">Se o assembly do tipo for conhecido, o carregador pesquisará os locais de redirecionamento do arquivo de configuração, o GAC, o assembly atual usando as informações de configuração e o diretório base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d832d-112">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="d832d-113">Se o assembly for desconhecido, o carregador pesquisará o assembly atual, mscorlib e o local retornado pelo manipulador `TypeResolve` de eventos.</span><span class="sxs-lookup"><span data-stu-id="d832d-113">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="d832d-114">Essa ordem de pesquisa do CLR pode ser modificada com ganchos, como o mecanismo de encaminhamento de tipo e o evento AppDomain. typeresolve.</span><span class="sxs-lookup"><span data-stu-id="d832d-114">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="d832d-115">Um invasor pode explorar a ordem de pesquisa do CLR e executar código não autorizado.</span><span class="sxs-lookup"><span data-stu-id="d832d-115">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="d832d-116">O uso de nomes totalmente qualificados (fortes) identifica exclusivamente um tipo e aumenta ainda mais a segurança do sistema.</span><span class="sxs-lookup"><span data-stu-id="d832d-116">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="d832d-117">Para obter mais informações, consulte [como o tempo de execução localiza assemblies](https://go.microsoft.com/fwlink/?LinkId=95336) e <xref:System.AppDomain.TypeResolve>.</span><span class="sxs-lookup"><span data-stu-id="d832d-117">For more information, see [How the Runtime Locates Assemblies](https://go.microsoft.com/fwlink/?LinkId=95336) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d832d-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d832d-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [<span data-ttu-id="d832d-119">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="d832d-119">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
