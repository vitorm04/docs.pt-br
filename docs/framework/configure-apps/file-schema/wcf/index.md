---
title: "Esquema de configuração do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7286793d6b2ad94c656dd37cdcc5fe1b0ab85660
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="09371-102">Esquema de configuração do WCF</span><span class="sxs-lookup"><span data-stu-id="09371-102">WCF Configuration Schema</span></span>
<span data-ttu-id="09371-103">Os elementos de configuração do [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] permitem que você configure aplicativos clientes e de serviço do [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09371-103">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] configuration elements enable you to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service and client applications.</span></span> <span data-ttu-id="09371-104">Você pode usar a [Ferramenta Editor de Configuração (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) para criar e modificar arquivos de configuração para clientes e serviços.</span><span class="sxs-lookup"><span data-stu-id="09371-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="09371-105">Como os arquivos de configuração são formatados como XML, você deverá estar familiarizado com XML se desejar editá-los manualmente usando um editor de texto.</span><span class="sxs-lookup"><span data-stu-id="09371-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="09371-106">Caso contrário, você pode ter problemas, como uma marca de elemento XML unfound ou atributo.</span><span class="sxs-lookup"><span data-stu-id="09371-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="09371-107">Isso ocorre porque marcas de elementos XML e atributos diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="09371-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="09371-108">O sistema de configuração do [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] baseia-se no namespace <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="09371-108">The [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="09371-109">Portanto, você pode usar todos os recursos padrão fornecidos pelo namespace <xref:System.Configuration>, como bloqueio de configuração, criptografia e mesclagem para aumentar a segurança de seu aplicativo e de sua configuração.</span><span class="sxs-lookup"><span data-stu-id="09371-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="09371-110">Para obter mais informações sobre esses conceitos, consulte os tópicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="09371-110">For more information on these concepts, see the following topics.</span></span>  
  
 [<span data-ttu-id="09371-111">Criptografando informações de configuração</span><span class="sxs-lookup"><span data-stu-id="09371-111">Encrypting Configuration Information</span></span>](http://go.microsoft.com/fwlink/?LinkId=95337)  
  
 <span data-ttu-id="09371-112">[Locking Configuration Settings](http://go.microsoft.com/fwlink/?LinkId=95338) (Bloqueando as definições de configuração)</span><span class="sxs-lookup"><span data-stu-id="09371-112">[Locking Configuration Settings](http://go.microsoft.com/fwlink/?LinkId=95338)</span></span>  
  
 <span data-ttu-id="09371-113">Esta seção descreve todos os possíveis valores de cada item de configuração e como eles interagem com outros elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="09371-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="09371-114">O mapa a seguir ilustra o esquema de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="09371-114">The following map illustrates the WCF configuration schema.</span></span>  
  
 <span data-ttu-id="09371-115">![Esquema de configuração do WCF](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span><span class="sxs-lookup"><span data-stu-id="09371-115">![WCF Configuration Schema](../../../../../docs/framework/configure-apps/file-schema/wcf/media/orcasconfigschema.gif "OrcasConfigSchema")</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="09371-116">Você deve proteger as seções de configuração do [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] em seus arquivos de configuração de aplicativo (app.config) com uma ACL (lista de controle de acesso) apropriada para evitar possíveis ameaças de segurança.</span><span class="sxs-lookup"><span data-stu-id="09371-116">You should protect [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="09371-117">Por exemplo, você deve garantir que somente pessoas apropriadas possam acessar ou modificar as configurações de segurança em associações de aplicativo ou a seção do modelo de serviço no arquivo de configuração de um serviço.</span><span class="sxs-lookup"><span data-stu-id="09371-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09371-118">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="09371-118">In This Section</span></span>  
 [<span data-ttu-id="09371-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="09371-119">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
 <span data-ttu-id="09371-120">Descreve o `ServiceModel` elemento.</span><span class="sxs-lookup"><span data-stu-id="09371-120">Describes the `ServiceModel` element.</span></span>  
  
 [<span data-ttu-id="09371-121">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="09371-121">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)  
 <span data-ttu-id="09371-122">Configura a ferramenta SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="09371-122">Configures the SMSvcHost.exe tool.</span></span>  
  
 [<span data-ttu-id="09371-123">\<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="09371-123">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
 <span data-ttu-id="09371-124">O elemento de nível superior para definir opções ao usar serializadores como o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="09371-124">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="09371-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="09371-125">Related Sections</span></span>  
 <span data-ttu-id="09371-126">[Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a) (Configurando aplicativos do Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="09371-126">[Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)</span></span>  
 <span data-ttu-id="09371-127">Descreve como configurar serviços e clientes do [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09371-127">Describes how to configure [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services and clients.</span></span>
