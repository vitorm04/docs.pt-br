---
title: Esquema de configuração do WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: 44d5e0acc6f5a9ca43949bce0c7964354ad18270
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91573651"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="bdd19-102">Esquema de configuração do WCF</span><span class="sxs-lookup"><span data-stu-id="bdd19-102">WCF Configuration Schema</span></span>

<span data-ttu-id="bdd19-103">Os elementos de configuração do Windows Communication Foundation (WCF) permitem configurar aplicativos cliente e serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="bdd19-103">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="bdd19-104">Você pode usar a [Ferramenta Editor de Configuração (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) para criar e modificar arquivos de configuração para clientes e serviços.</span><span class="sxs-lookup"><span data-stu-id="bdd19-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="bdd19-105">Como os arquivos de configuração são formatados como XML, você deverá estar familiarizado com XML se desejar editá-los manualmente usando um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="bdd19-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="bdd19-106">Caso contrário, você pode ter problemas, como uma marca de elemento XML unfound ou atributo.</span><span class="sxs-lookup"><span data-stu-id="bdd19-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="bdd19-107">Isso ocorre porque marcas de elementos XML e atributos diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="bdd19-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="bdd19-108">O sistema de configuração do WCF é baseado no <xref:System.Configuration> namespace.</span><span class="sxs-lookup"><span data-stu-id="bdd19-108">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="bdd19-109">Portanto, você pode usar todos os recursos padrão fornecidos pelo namespace <xref:System.Configuration>, como bloqueio de configuração, criptografia e mesclagem para aumentar a segurança de seu aplicativo e de sua configuração.</span><span class="sxs-lookup"><span data-stu-id="bdd19-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="bdd19-110">Para obter mais informações sobre esses conceitos, consulte os tópicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="bdd19-110">For more information on these concepts, see the following topics.</span></span>  
  
 <span data-ttu-id="bdd19-111">[Criptografando informações de configuração](/previous-versions/aspnet/53tyfkaw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bdd19-111">[Encrypting Configuration Information](/previous-versions/aspnet/53tyfkaw(v=vs.100))</span></span>  
  
 <span data-ttu-id="bdd19-112">[Locking Configuration Settings](/previous-versions/aspnet/55th21y4(v=vs.100)) (Bloqueando as definições de configuração)</span><span class="sxs-lookup"><span data-stu-id="bdd19-112">[Locking Configuration Settings](/previous-versions/aspnet/55th21y4(v=vs.100))</span></span>  
  
 <span data-ttu-id="bdd19-113">Esta seção descreve todos os possíveis valores de cada item de configuração e como eles interagem com outros elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="bdd19-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="bdd19-114">O mapa a seguir ilustra o esquema de configuração do WCF:</span><span class="sxs-lookup"><span data-stu-id="bdd19-114">The following map illustrates the WCF configuration schema:</span></span>

:::image type="content" source="./media/index/windows-communication-foundation-configuration-schema.gif" alt-text="Diagrama que mostra o esquema de configuração do WCF." lightbox="./media/index/windows-communication-foundation-configuration-schema.gif":::
  
> [!CAUTION]
> <span data-ttu-id="bdd19-116">Proteja as seções de configuração do WCF em seus arquivos de configuração de aplicativo (app.config) com ACLs (listas de controle de acesso) apropriadas para evitar possíveis ameaças de segurança.</span><span class="sxs-lookup"><span data-stu-id="bdd19-116">Protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span> <span data-ttu-id="bdd19-117">Por exemplo, certifique-se de que apenas as pessoas apropriadas possam acessar ou modificar as configurações de segurança em associações de aplicativo ou a seção de modelo de serviço do arquivo de configuração para um serviço.</span><span class="sxs-lookup"><span data-stu-id="bdd19-117">For example, make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bdd19-118">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="bdd19-118">In This Section</span></span>  

 [\<system.serviceModel>](system-servicemodel.md)  
 <span data-ttu-id="bdd19-119">Descreve o `ServiceModel` elemento.</span><span class="sxs-lookup"><span data-stu-id="bdd19-119">Describes the `ServiceModel` element.</span></span>  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 <span data-ttu-id="bdd19-120">Configura a ferramenta SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="bdd19-120">Configures the SMSvcHost.exe tool.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 <span data-ttu-id="bdd19-121">O elemento de nível superior para definir opções ao usar serializadores como o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="bdd19-121">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bdd19-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="bdd19-122">Related Sections</span></span>  

 <span data-ttu-id="bdd19-123">[Configuring Windows Communication Foundation Applications](../../../wcf/configuring-services.md) (Configurando aplicativos do Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="bdd19-123">[Configuring Windows Communication Foundation Applications](../../../wcf/configuring-services.md)</span></span>  
 <span data-ttu-id="bdd19-124">Descreve como configurar clientes e serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="bdd19-124">Describes how to configure WCF services and clients.</span></span>
