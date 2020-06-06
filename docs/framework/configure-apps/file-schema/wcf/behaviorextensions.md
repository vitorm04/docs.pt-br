---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: 39dc92d65a41d223ebd39aec3dc59871ad1fd101
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448679"
---
# \<behaviorExtensions>
<span data-ttu-id="77ac9-101">As extensões de comportamento permitem que o usuário crie elementos de comportamento definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="77ac9-101">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="77ac9-102">Esses elementos podem ser usados junto com os elementos de comportamento padrão do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="77ac9-102">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="77ac9-103">A `behaviorExtensions` seção define o elemento de modo que ele possa ser usado na configuração.</span><span class="sxs-lookup"><span data-stu-id="77ac9-103">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="77ac9-104">Aqui está um exemplo de uma extensão de comportamento típica.</span><span class="sxs-lookup"><span data-stu-id="77ac9-104">Here is an example of a typical behavior extension.</span></span>  
  
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
  
 <span data-ttu-id="77ac9-105">Para adicionar habilidades de configuração ao elemento, você precisa escrever e registrar um elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="77ac9-105">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="77ac9-106">Para obter mais informações sobre isso, consulte a <xref:System.Configuration> documentação.</span><span class="sxs-lookup"><span data-stu-id="77ac9-106">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="77ac9-107">Depois que o elemento e seu tipo de configuração são definidos, a extensão pode ser usada, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="77ac9-107">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
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
  
## <a name="security"></a><span data-ttu-id="77ac9-108">Segurança</span><span class="sxs-lookup"><span data-stu-id="77ac9-108">Security</span></span>  
 <span data-ttu-id="77ac9-109">É altamente recomendável que você use nomes de assembly totalmente qualificados ao registrar tipos nos `machine.config` arquivos e `app.config` .</span><span class="sxs-lookup"><span data-stu-id="77ac9-109">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="77ac9-110">Se o tipo não for definido exclusivamente, o carregador de tipo CLR pesquisará nos seguintes locais na ordem especificada:</span><span class="sxs-lookup"><span data-stu-id="77ac9-110">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="77ac9-111">Se o assembly do tipo for conhecido, o carregador pesquisará os locais de redirecionamento do arquivo de configuração, o GAC, o assembly atual usando as informações de configuração e o diretório base do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="77ac9-111">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="77ac9-112">Se o assembly for desconhecido, o carregador pesquisará o assembly atual, mscorlib e o local retornado pelo `TypeResolve` manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="77ac9-112">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="77ac9-113">Essa ordem de pesquisa do CLR pode ser modificada com ganchos como o mecanismo de encaminhamento de tipo e o evento AppDomain. TypeResolve.</span><span class="sxs-lookup"><span data-stu-id="77ac9-113">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="77ac9-114">Um invasor pode explorar a ordem de pesquisa do CLR e executar código não autorizado.</span><span class="sxs-lookup"><span data-stu-id="77ac9-114">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="77ac9-115">Usar nomes totalmente qualificados (fortes) identifica exclusivamente um tipo e aumenta ainda mais a segurança do sistema.</span><span class="sxs-lookup"><span data-stu-id="77ac9-115">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="77ac9-116">Para obter mais informações, consulte [como o tempo de execução localiza assemblies](../../../deployment/how-the-runtime-locates-assemblies.md) e <xref:System.AppDomain.TypeResolve> .</span><span class="sxs-lookup"><span data-stu-id="77ac9-116">For more information, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ac9-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="77ac9-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [<span data-ttu-id="77ac9-118">Configurando e estendendo o runtime com comportamentos</span><span class="sxs-lookup"><span data-stu-id="77ac9-118">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
