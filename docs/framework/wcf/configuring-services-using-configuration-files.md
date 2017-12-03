---
title: "Configurando serviços usando arquivos de configuração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4decb820f012d3f4b2a9855cd08701f14dcc5431
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="962e6-102">Configurando serviços usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="962e6-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="962e6-103">Configurar um serviço [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] com um arquivo de configuração oferece flexibilidade para fornecer dados do comportamento do ponto de extremidade e do serviço na hora da implantação em vez de em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="962e6-103">Configuring a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="962e6-104">Este tópico descreve as principais técnicas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="962e6-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="962e6-105">Um serviço [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] é configurável usando a tecnologia de configuração do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="962e6-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="962e6-106">Mais comumente, os elementos XML são adicionados ao arquivo Web.config para um site do IIS (Serviços de Informações da Internet) que hospeda um serviço [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="962e6-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="962e6-107">Os elementos permitem que você altere detalhes, como os endereços de ponto de extremidade (endereços reais usados para comunicação com o serviço) de cada computador.</span><span class="sxs-lookup"><span data-stu-id="962e6-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="962e6-108">Além disso, o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] inclui vários elementos fornecidos pelo sistema que permitem selecionar rapidamente os recursos mais básicos para um serviço.</span><span class="sxs-lookup"><span data-stu-id="962e6-108">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="962e6-109">A partir do [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] é fornecido com um novo modelo de configuração padrão que simplifica os requisitos de configuração do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="962e6-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comes with a new default configuration model that simplifies [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration requirements.</span></span> <span data-ttu-id="962e6-110">Se você não fornecer nenhuma configuração do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] para um determinado serviço, o tempo de execução configurará seu serviço automaticamente com alguns pontos de extremidade e associação/comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="962e6-110">If you do not provide any [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="962e6-111">Na prática, gravar a configuração é a maior parte da programação de aplicativos [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="962e6-111">In practice, writing configuration is a major part of programming [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications.</span></span>  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="962e6-112">[Configurando associações para serviços](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="962e6-112"> [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span> [!INCLUDE[crlist](../../../includes/crlist-md.md)]<span data-ttu-id="962e6-113">os elementos mais usados, consulte [System-Provided associações](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="962e6-113"> of the most commonly used elements, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="962e6-114">pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="962e6-114"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="962e6-115">Ao implantar os cenários lado a lado onde duas versões diferentes de um serviço são implantadas, é necessário especificar nomes parciais de assemblies referenciados em arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="962e6-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="962e6-116">Isso ocorre porque o arquivo de configuração é compartilhado entre todas as versões de um serviço e pode estar em execução em versões diferentes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="962e6-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="962e6-117">System.Configuration: Web.config e App.config</span><span class="sxs-lookup"><span data-stu-id="962e6-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="962e6-118">O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usa o sistema de configuração System.Configuration do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="962e6-118">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uses the System.Configuration configuration system of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="962e6-119">Ao configurar um serviço no [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], use um arquivo Web.config ou um arquivo App.config para especificar as configurações.</span><span class="sxs-lookup"><span data-stu-id="962e6-119">When configuring a service in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="962e6-120">A escolha do nome do arquivo de configuração é determinada pelo ambiente de hospedagem que você escolhe para o serviço.</span><span class="sxs-lookup"><span data-stu-id="962e6-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="962e6-121">Se você estiver usando o IIS para hospedar o serviço, use um arquivo Web.config.</span><span class="sxs-lookup"><span data-stu-id="962e6-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="962e6-122">Se você estiver usando qualquer outro ambiente de hospedagem, use um arquivo App.config.</span><span class="sxs-lookup"><span data-stu-id="962e6-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="962e6-123">No [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], o arquivo denominado App.config é usado para criar o arquivo de configuração final.</span><span class="sxs-lookup"><span data-stu-id="962e6-123">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="962e6-124">O nome final realmente usado para a configuração depende do nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="962e6-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="962e6-125">Por exemplo, um assembly denominado "Cohowinery.exe" tem um nome de arquivo de configuração final de "Cohowinery.exe.config".</span><span class="sxs-lookup"><span data-stu-id="962e6-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="962e6-126">Entretanto, você precisa modificar somente o arquivo App.config.</span><span class="sxs-lookup"><span data-stu-id="962e6-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="962e6-127">As alterações feitas nesse arquivo são automaticamente feitas no arquivo de configuração final do aplicativo em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="962e6-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="962e6-128">Ao usar um arquivo App.config, o sistema de configuração mescla o arquivo App.config com o conteúdo do arquivo Machine.config quando o aplicativo é iniciado e a configuração é aplicada.</span><span class="sxs-lookup"><span data-stu-id="962e6-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="962e6-129">Esse mecanismo permite que as configurações de todo o computador sejam definidas no arquivo Machine.config.</span><span class="sxs-lookup"><span data-stu-id="962e6-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="962e6-130">O arquivo App.config pode ser usado para substituir as configurações do arquivo Machine.config. Você também pode bloquear as configurações no arquivo Machine.config para que sejam usadas.</span><span class="sxs-lookup"><span data-stu-id="962e6-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="962e6-131">No caso do Web.config, o sistema de configuração mescla os arquivos Web.config em todos os diretórios que levam ao diretório do aplicativo na configuração que é aplicada.</span><span class="sxs-lookup"><span data-stu-id="962e6-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="962e6-132"> as prioridades de configuração, consulte os tópicos no namespace <xref:System.Configuration>.</span><span class="sxs-lookup"><span data-stu-id="962e6-132"> configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="962e6-133">Seções principais do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="962e6-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="962e6-134">As seções principais do arquivo de configuração incluem os seguintes elementos.</span><span class="sxs-lookup"><span data-stu-id="962e6-134">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!—- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->   
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="962e6-135">As seções de associações e de comportamentos são opcionais e são incluídas apenas se necessário.</span><span class="sxs-lookup"><span data-stu-id="962e6-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="962e6-136">O \<services > elemento</span><span class="sxs-lookup"><span data-stu-id="962e6-136">The \<services> Element</span></span>  
 <span data-ttu-id="962e6-137">O elemento `services` contém as especificações de todos os serviços que o aplicativo hospeda.</span><span class="sxs-lookup"><span data-stu-id="962e6-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="962e6-138">A partir do modelo de configuração simplificada no [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], esta seção é opcional.</span><span class="sxs-lookup"><span data-stu-id="962e6-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="962e6-139">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="962e6-139">\<services></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="962e6-140">O \<service > elemento</span><span class="sxs-lookup"><span data-stu-id="962e6-140">The \<service> Element</span></span>  
 <span data-ttu-id="962e6-141">Cada serviço tem os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="962e6-141">Each service has these attributes:</span></span>  
  
-   <span data-ttu-id="962e6-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="962e6-142">`name`.</span></span> <span data-ttu-id="962e6-143">Especifica o tipo que fornece uma implementação de um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="962e6-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="962e6-144">É um nome totalmente qualificado que consiste no namespace, em um ponto e no nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="962e6-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="962e6-145">Por exemplo `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="962e6-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
-   <span data-ttu-id="962e6-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="962e6-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="962e6-147">Especifica o nome de um dos elementos `behavior` localizados no elemento `behaviors`.</span><span class="sxs-lookup"><span data-stu-id="962e6-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="962e6-148">O comportamento especificado governa as ações, como, por exemplo, se o serviço permite representação.</span><span class="sxs-lookup"><span data-stu-id="962e6-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="962e6-149">Se seu valor for o nome vazio ou se nenhum `behaviorConfiguration` for fornecido, o conjunto padrão de comportamentos de serviço será adicionado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="962e6-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
-   [<span data-ttu-id="962e6-150">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="962e6-150">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="962e6-151">O \<ponto de extremidade > elemento</span><span class="sxs-lookup"><span data-stu-id="962e6-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="962e6-152">Cada ponto de extremidade requer um endereço, uma associação e um contrato, que são representados pelos seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="962e6-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
-   <span data-ttu-id="962e6-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="962e6-153">`address`.</span></span> <span data-ttu-id="962e6-154">Especifica o URI (Uniform Resource Identifier) do serviço, que pode ser um endereço absoluto ou um endereço fornecido em relação ao endereço básico do serviço.</span><span class="sxs-lookup"><span data-stu-id="962e6-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="962e6-155">Se definido como uma cadeia de caracteres vazia, indicará que o ponto de extremidade está disponível no endereço básico especificado ao criar <xref:System.ServiceModel.ServiceHost> do serviço.</span><span class="sxs-lookup"><span data-stu-id="962e6-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
-   <span data-ttu-id="962e6-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="962e6-156">`binding`.</span></span> <span data-ttu-id="962e6-157">Normalmente especifica uma associação fornecida pelo sistema, como <xref:System.ServiceModel.WSHttpBinding>, mas também pode especificar uma associação definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="962e6-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="962e6-158">A associação especificada determina o tipo de transporte, de segurança e de codificação usado, e se sessões confiáveis, transações ou streaming são suportados ou se estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="962e6-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
-   <span data-ttu-id="962e6-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="962e6-159">`bindingConfiguration`.</span></span> <span data-ttu-id="962e6-160">Se os valores padrão de uma associação precisarem ser modificados, isso poderá ser feito configurando o elemento `binding` apropriado no elemento `bindings`.</span><span class="sxs-lookup"><span data-stu-id="962e6-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="962e6-161">Esse atributo deve receber o mesmo valor que o atributo `name` do elemento `binding` que é usado para alterar os padrões.</span><span class="sxs-lookup"><span data-stu-id="962e6-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="962e6-162">Se nenhum nome for fornecido, ou se nenhum `bindingConfiguration` estiver especificado na associação, a associação padrão do tipo de associação será usada no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="962e6-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
-   <span data-ttu-id="962e6-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="962e6-163">`contract`.</span></span> <span data-ttu-id="962e6-164">Especifica a interface que define o contrato.</span><span class="sxs-lookup"><span data-stu-id="962e6-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="962e6-165">Essa é a interface implementada no tipo CLR (Common Language Runtime) especificado pelo atributo `name` do elemento `service`.</span><span class="sxs-lookup"><span data-stu-id="962e6-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
-   [<span data-ttu-id="962e6-166">\<ponto de extremidade > Referência de elemento</span><span class="sxs-lookup"><span data-stu-id="962e6-166">\<endpoint> element reference</span></span>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="962e6-167">O \<associações > elemento</span><span class="sxs-lookup"><span data-stu-id="962e6-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="962e6-168">O elemento `bindings` contém as especificações de todas as associações que podem ser usadas por qualquer ponto de extremidade definido em qualquer serviço.</span><span class="sxs-lookup"><span data-stu-id="962e6-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="962e6-169">\<associações ></span><span class="sxs-lookup"><span data-stu-id="962e6-169">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="962e6-170">O \<associação > elemento</span><span class="sxs-lookup"><span data-stu-id="962e6-170">The \<binding> Element</span></span>  
 <span data-ttu-id="962e6-171">O `binding` elementos contidos no `bindings` elemento pode ser qualquer uma das associações fornecidas pelo sistema (consulte [System-Provided associações](../../../docs/framework/wcf/system-provided-bindings.md)) ou uma associação personalizada (consulte [associações personalizadas](../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="962e6-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) or a custom binding (see [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="962e6-172">O elemento `binding` tem um atributo `name` que correlaciona a associação ao ponto de extremidade especificado no atributo `bindingConfiguration` do elemento `endpoint`.</span><span class="sxs-lookup"><span data-stu-id="962e6-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="962e6-173">Se nenhum nome for especificado, a associação corresponderá ao padrão desse tipo de associação.</span><span class="sxs-lookup"><span data-stu-id="962e6-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="962e6-174">Configurar serviços e clientes, consulte [Configurando o Windows Communication Foundation aplicativos](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span><span class="sxs-lookup"><span data-stu-id="962e6-174"> configuring services and clients, see [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
 [<span data-ttu-id="962e6-175">\<associação ></span><span class="sxs-lookup"><span data-stu-id="962e6-175">\<binding></span></span>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="962e6-176">O \<comportamentos > elemento</span><span class="sxs-lookup"><span data-stu-id="962e6-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="962e6-177">Esse é um elemento contêiner dos elementos `behavior` que definem os comportamentos de um serviço.</span><span class="sxs-lookup"><span data-stu-id="962e6-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="962e6-178">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="962e6-178">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="962e6-179">O \<comportamento > elemento</span><span class="sxs-lookup"><span data-stu-id="962e6-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="962e6-180">Cada `behavior` elemento é identificado por um `name` de atributo e fornece o comportamento fornecido pelo sistema, como <`throttling`>, ou um comportamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="962e6-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="962e6-181">Se nenhum nome for fornecido, esse elemento de comportamento corresponderá ao comportamento padrão do serviço ou do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="962e6-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="962e6-182">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="962e6-182">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="962e6-183">Como usar as configurações de associação e de comportamento</span><span class="sxs-lookup"><span data-stu-id="962e6-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="962e6-184">O [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] facilita o compartilhamento das configurações entre pontos de extremidade usando um sistema de referência na configuração.</span><span class="sxs-lookup"><span data-stu-id="962e6-184">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="962e6-185">Em vez de atribuir valores de configuração diretamente a um ponto de extremidade, os valores da configuração relacionados à associação são agrupados em elementos `bindingConfiguration` na seção `<binding>`.</span><span class="sxs-lookup"><span data-stu-id="962e6-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="962e6-186">A configuração de uma associação é um grupo nomeado de configurações em uma associação.</span><span class="sxs-lookup"><span data-stu-id="962e6-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="962e6-187">Os pontos de extremidade podem fazer referência a `bindingConfiguration` por nome.</span><span class="sxs-lookup"><span data-stu-id="962e6-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!—- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint   
          address="myAddress" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint   
          address="myAddress2" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint   
          address="myAddress3" binding="basicHttpBinding"   
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="962e6-188">O `name` de `bindingConfiguration` é definido no elemento `<binding>`.</span><span class="sxs-lookup"><span data-stu-id="962e6-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="962e6-189">O `name` deve ser uma cadeia de caracteres exclusiva dentro do escopo do tipo binding — neste caso o [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), ou um valor vazio para referir-se a associação padrão.</span><span class="sxs-lookup"><span data-stu-id="962e6-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="962e6-190">O ponto de extremidade vincula-se à configuração definindo o atributo `bindingConfiguration` para essa cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="962e6-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="962e6-191">Um `behaviorConfiguration` é implementado da mesma forma, conforme ilustrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="962e6-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint   
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="962e6-192">Observe que o conjunto padrão de comportamentos de serviço é adicionado ao serviço.</span><span class="sxs-lookup"><span data-stu-id="962e6-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="962e6-193">Esse sistema permite que os pontos de extremidade compartilhem configurações comuns sem redefinir as configurações.</span><span class="sxs-lookup"><span data-stu-id="962e6-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="962e6-194">Se o escopo de todo o computador for necessário, crie a configuração de associação ou de comportamento no Machine.config. Os parâmetros de configuração estão disponíveis em todos os arquivos App.config.</span><span class="sxs-lookup"><span data-stu-id="962e6-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="962e6-195">O [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) torna mais fácil criar configurações.</span><span class="sxs-lookup"><span data-stu-id="962e6-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="962e6-196">Mesclagem de comportamentos</span><span class="sxs-lookup"><span data-stu-id="962e6-196">Behavior Merge</span></span>  
 <span data-ttu-id="962e6-197">O recurso de mesclagem de comportamentos facilita o gerenciamento dos comportamentos quando você deseja que um conjunto de comportamentos comuns sejam usados de maneira consistente.</span><span class="sxs-lookup"><span data-stu-id="962e6-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="962e6-198">Esse recurso permite que você especifique comportamentos em diferentes níveis da hierarquia de configuração e faça com que os serviços herdem comportamentos de vários níveis da hierarquia de configuração.</span><span class="sxs-lookup"><span data-stu-id="962e6-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="962e6-199">Para ilustrar como isso funciona, suponha que você tenha o seguinte layout de diretório virtual no IIS:</span><span class="sxs-lookup"><span data-stu-id="962e6-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 <span data-ttu-id="962e6-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span><span class="sxs-lookup"><span data-stu-id="962e6-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span></span>  
  
 <span data-ttu-id="962e6-201">E o arquivo ~\Web.config possui o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="962e6-201">And your ~\Web.config file has the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="962e6-202">E você tem um Web.config filho localizado em ~\Child\Web.config com o seguinte conteúdo:</span><span class="sxs-lookup"><span data-stu-id="962e6-202">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="962e6-203">O serviço localizado em ~\Child\Service.svc se comportará como se tivesse os comportamentos de serviceDebug e de serviceMetadata.</span><span class="sxs-lookup"><span data-stu-id="962e6-203">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="962e6-204">O serviço localizado em ~ \ Service.svc só terá o comportamento de serviceDebug.</span><span class="sxs-lookup"><span data-stu-id="962e6-204">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="962e6-205">O que acontece é que as duas coleções de comportamentos com o mesmo nome (neste caso a cadeia de caracteres vazia) são mescladas.</span><span class="sxs-lookup"><span data-stu-id="962e6-205">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="962e6-206">Também é possível limpar as coleções de comportamento usando o \<limpar > marca e removido comportamentos individuais da coleção usando o \<remover > marca.</span><span class="sxs-lookup"><span data-stu-id="962e6-206">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="962e6-207">Por exemplo, as duas configurações a seguir resultam no serviço filho que tem apenas o comportamento de serviceMetadata:</span><span class="sxs-lookup"><span data-stu-id="962e6-207">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="962e6-208">A mesclagem de comportamentos é feita para coleções de comportamentos sem nome, conforme mostrado acima, e também para coleções de comportamentos nomeadas.</span><span class="sxs-lookup"><span data-stu-id="962e6-208">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="962e6-209">A mesclagem de comportamentos funciona no ambiente de hospedagem do IIS, no qual os arquivos Web.config são mesclados hierarquicamente com o arquivo Web.config raiz e o machine.config. Mas isso também funciona no ambiente do aplicativo, onde o machine.config pode ser mesclado com o arquivo App.config.</span><span class="sxs-lookup"><span data-stu-id="962e6-209">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="962e6-210">A mesclagem de comportamentos se aplica aos comportamentos de ponto de extremidade e aos comportamentos de serviço na configuração.</span><span class="sxs-lookup"><span data-stu-id="962e6-210">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="962e6-211">Se uma coleção de comportamentos filho contiver um comportamento que já esteja presente na coleção de comportamentos pai, o comportamento filho substituirá o pai.</span><span class="sxs-lookup"><span data-stu-id="962e6-211">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="962e6-212">Portanto, se uma coleção de comportamento pai tinha `<serviceMetadata httpGetEnabled="False" />` e uma coleção de comportamento filho tinha `<serviceMetadata httpGetEnabled="True" />`, o comportamento de filho poderia substituir o comportamento do pai da coleção de comportamento e httpGetEnabled seria "true".</span><span class="sxs-lookup"><span data-stu-id="962e6-212">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="962e6-213">Consulte também</span><span class="sxs-lookup"><span data-stu-id="962e6-213">See Also</span></span>  
 <span data-ttu-id="962e6-214">[Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) (Configuração simplificada)</span><span class="sxs-lookup"><span data-stu-id="962e6-214">[Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
 <span data-ttu-id="962e6-215">[Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a) (Configurando aplicativos do Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="962e6-215">[Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)</span></span>  
 [<span data-ttu-id="962e6-216">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="962e6-216">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [<span data-ttu-id="962e6-217">\<associação ></span><span class="sxs-lookup"><span data-stu-id="962e6-217">\<binding></span></span>](../../../docs/framework/misc/binding.md)
