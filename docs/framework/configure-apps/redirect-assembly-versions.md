---
title: Redirecionando versões de assembly
ms.date: 03/30/2017
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3459ebd2f1df38ac70e9211fd4865e227cd996cb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759264"
---
# <a name="redirecting-assembly-versions"></a>Redirecionando versões de assembly
Você pode redirecionar referências de associação de tempo de compilação para assemblies do .NET Framework, os assemblies de terceiros ou assemblies do seu próprio aplicativo. Você pode redirecionar seu aplicativo para usar uma versão diferente de um assembly de várias maneiras: por meio da política de publicador, por meio de um arquivo de configuração do aplicativo. ou por meio do arquivo de configuração de máquina. Este artigo descreve o funcionamento de associação de assembly do .NET Framework e como ele pode ser configurado.  
  
<a name="BKMK_Assemblyunificationanddefaultbinding"></a>   
## <a name="assembly-unification-and-default-binding"></a>União de assembly e associação padrão  
 Associações de assemblies do .NET Framework são redirecionadas, às vezes, por meio de um processo chamado *Unificação de assembly*. O .NET Framework consiste em uma versão do common language runtime e assemblies do .NET Framework aproximadamente 24 que compõem a biblioteca de tipos. Esses assemblies do .NET Framework são tratados pelo tempo de execução como uma única unidade. Por padrão, quando um aplicativo é iniciado, todas as referências aos tipos em código executado pelo tempo de execução são direcionadas para os assemblies do .NET Framework que têm o mesmo número de versão que o tempo de execução que é carregado em um processo. Os redirecionamentos que ocorrem com esse modelo são o comportamento padrão para o tempo de execução.  
  
 Por exemplo, se seu aplicativo referenciar tipos no namespace System XML e foi criado usando o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ele contém uma referência estática para o assembly System. XML que acompanha a versão 4.5 do tempo de execução. Se você deseja redirecionar a referência de associação para apontar para o assembly System. XML que são fornecidos com o .NET Framework 4, você pode colocar informações de redirecionamento no arquivo de configuração do aplicativo. Um redirecionamento de associação em um arquivo de configuração para um assembly do .NET Framework unificado cancela a Unificação para esse assembly.  
  
 Além disso, você talvez queira redirecionar manualmente a associação para assemblies de terceiros, se houver várias versões de assembly.  
  
<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>   
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Redirecionando versões de assembly usando a política de publicador  
 Fornecedores de assemblies podem direcionar os aplicativos para uma versão mais recente de um assembly, incluindo um arquivo de política do publicador com o novo assembly. O arquivo de política de publicador, que está localizado no cache de assembly global, contém as configurações de redirecionamento de assembly.  
  
 Cada *principais*. *pequenas* versão de um assembly tem seu próprio arquivo de política do publicador. Por exemplo, redirecionamentos de versão 2.0.2.222 para 2.0.3.000 e da versão 2.0.2.321 a versão 2.0.3.000 ambos ir para o mesmo arquivo, porque eles estão associados com a versão 2.0. No entanto, um redirecionamento de versão 3.0.0.999 versão 4.0.0.000 vai para o arquivo para a versão 3.0.999. Cada versão principal do .NET Framework tem seu próprio arquivo de política do publicador.  
  
 Se existir um arquivo de política de publicador para um assembly, o tempo de execução verifica esse arquivo depois de verificar o arquivo de configuração de aplicativo e de manifesto do assembly. Fornecedores devem usar arquivos de política de publicador somente quando o novo assembly é compatível com o assembly que está sendo redirecionado.  
  
 Você pode ignorar diretiva publisher para seu aplicativo, especificando as configurações no arquivo de configuração do aplicativo, conforme discutido no [ignorando seção de diretiva publisher](#bypass_PP).  
  
<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>   
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Redirecionando versões de assembly no nível do aplicativo  
 Há algumas técnicas diferentes para alterar o comportamento de associação para seu aplicativo por meio do arquivo de configuração do aplicativo: você pode editar manualmente o arquivo, você pode contar com redirecionamento de associação automática ou você pode especificar o comportamento de associação, ignorando a política de editor.  
  
### <a name="manually-editing-the-app-config-file"></a>Editar manualmente o arquivo de configuração do aplicativo  
 Você pode editar manualmente o arquivo de configuração do aplicativo para resolver problemas de assembly. Por exemplo, se um fornecedor pode lançar uma versão mais recente de um assembly que o aplicativo usa sem fornecer uma política de editor, pois elas não garantem a compatibilidade com versões anteriores, você pode direcionar o aplicativo para usar a versão mais recente do assembly, colocando o assembly associando informações no arquivo de configuração do aplicativo da seguinte maneira.  
  
```xml  
<dependentAssembly>  
  <assemblyIdentity name="someAssembly"  
    publicKeyToken="32ab4ba45e0a69a1"  
    culture="en-us" />  
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />  
</dependentAssembly>  
```  
  
### <a name="relying-on-automatic-binding-redirection"></a>Depender de redirecionamento de associação automática  
 Começando com [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], novos aplicativos de área de trabalho que se destinam a [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] usar redirecionamento de associação automática. Isso significa que se dois componentes referenciam versões diferentes do mesmo assembly de nome forte, o tempo de execução adiciona automaticamente um redirecionamento de associação para a versão mais recente do assembly no arquivo de configuração (App. config) do aplicativo de saída. Esse redirecionamento substitui a união de assembly que pode levar caso contrário, o local. O arquivo de origem app.config não é modificado. Por exemplo, digamos que seu aplicativo diretamente referencia um componente do .NET Framework fora de banda, mas usa uma biblioteca de terceiros que tem como alvo uma versão mais antiga do mesmo componente. Quando você compilar o aplicativo, o arquivo de configuração do aplicativo de saída é modificado para conter um redirecionamento de associação para a versão mais recente do componente. Se você criar um aplicativo web, você receberá um aviso de compilação sobre o conflito de associação, que por sua vez, oferece a opção para adicionar o redirecionamento de associação necessários para o arquivo de configuração da web de origem.  
  
 Se você adicionar manualmente redirecionamentos de ligação ao arquivo App. config de origem, no tempo de compilação, [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] tenta unificar os assemblies com base nos redirecionamentos de associação que você adicionou. Por exemplo, digamos que você inserir o seguinte redirecionamento de associação para um assembly:  
  
 `<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`  
  
 Se a versão 1.0.0.0 do mesmo assembly faz referência a outro projeto em seu aplicativo, o redirecionamento de associação automática adiciona a seguinte entrada ao arquivo App. config de saída para que o aplicativo é unificado na versão 2.0.0.0 deste assembly:  
  
 `<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`  
  
 Você pode habilitar o redirecionamento de associação automática se seu aplicativo tem como alvo as versões mais antigas do .NET Framework em [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]. Você pode substituir esse comportamento padrão, fornecendo as informações de redirecionamento de associação no arquivo App. config para qualquer conjunto ou desativar o recurso de redirecionamento de associação. Para obter informações sobre como ativar ou desativar o esse recurso, consulte [como: habilitar e desabilitar o redirecionamento de associação automática](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).  
  
<a name="bypass_PP"></a>   
### <a name="bypassing-publisher-policy"></a>Ignorando a política de editor  
 Você pode substituir a política de editor no arquivo de configuração do aplicativo, se necessário. Por exemplo, novas versões de assemblies que alegam ser compatível com versões anteriores ainda podem interromper um aplicativo. Se você quiser ignorar a política de editor, adicione um [ \<publisherPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elemento para o [ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) elemento no arquivo de configuração do aplicativo e o conjunto de **aplicar** atributo **sem**, que substitui qualquer anterior **Sim** configurações.  
  
 `<publisherPolicy apply="no" />`  
  
 Ignorar diretiva publisher para manter seu aplicativo em execução para os usuários, mas certifique-se de que relatar o problema para o fornecedor do assembly. Se um assembly tem um arquivo de política de editor, o fornecedor deve garantir que o assembly é compatível com versões anteriores e que os clientes podem usar a nova versão tanto quanto possível.  
  
<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>   
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Redirecionando versões de assembly no nível do computador  
 Pode haver casos raros quando quiser que todos os aplicativos em um computador para usar uma versão específica de um assembly a um administrador do computador. Por exemplo, o administrador possa querer que todos os aplicativos para usar uma versão específica de assembly, porque essa versão corrige uma falha de segurança. Se um assembly é redirecionado no arquivo de configuração da máquina, todos os aplicativos na máquina que usam a versão antiga serão direcionados para usar a nova versão. O arquivo de configuração de máquina substitui o arquivo de configuração do aplicativo e o arquivo de política do publicador. Esse arquivo está localizado no diretório %*runtime install path*%\Config. Normalmente, o .NET Framework é instalado no diretório %drive%\Windows\Microsoft.NET\Framework.  
  
<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>   
## <a name="specifying-assembly-binding-in-configuration-files"></a>Especificando arquivos de configuração de associação de assembly  
 Você pode usar o mesmo formato XML para especificar redirecionamentos de associação, se ele está no arquivo de configuração do aplicativo, o arquivo de configuração de máquina ou o arquivo de política do publicador. Para redirecionar uma versão de assembly para outro, use o [ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md) elemento. O **oldVersion** atributo pode especificar uma versão de assembly único ou um intervalo de versões. O `newVersion` atributo deve especificar uma única versão.  Por exemplo, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` Especifica que o tempo de execução deve usar a versão 2.0.0.0 em vez das versões de assembly entre 1.1.0.0 e 1.2.0.0.  
  
 O exemplo de código a seguir demonstra uma variedade de cenários de redirecionamento de associação. O exemplo especifica um redirecionamento para um intervalo de versões para `myAssembly`e um redirecionamento de associação simples para `mySecondAssembly`. O exemplo também especifica esse arquivo de política do publicador não substituirá os redirecionamentos de associação para `myThirdAssembly`.  
  
 Para associar um assembly, você deve especificar a cadeia de caracteres "urn: schemas-microsoft-v1" com o **xmlns** atributo o [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) marca.  
  
```xml  
<configuration>  
  <runtime>  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
      <dependentAssembly>  
        <assemblyIdentity name="myAssembly"  
          publicKeyToken="32ab4ba45e0a69a1"  
          culture="en-us" />  
        <!-- Assembly versions can be redirected in app,   
          publisher policy, or machine configuration files. -->  
        <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="3.0.0.0" />  
      </dependentAssembly>  
  <dependentAssembly>  
        <assemblyIdentity name="mySecondAssembly"  
          publicKeyToken="32ab4ba45e0a69a1"  
          culture="en-us" />  
             <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />  
      </dependentAssembly>  
      <dependentAssembly>  
      <assemblyIdentity name="myThirdAssembly"  
        publicKeyToken="32ab4ba45e0a69a1"  
        culture="en-us" />  
        <!-- Publisher policy can be set only in the app   
          configuration file. -->  
        <publisherPolicy apply="no" />  
      </dependentAssembly>  
    </assemblyBinding>  
  </runtime>  
</configuration>  
```  
  
### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Limitando as associações de assembly para uma versão específica  
 Você pode usar o **appliesTo** atributo no [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) elemento em um arquivo de configuração do aplicativo para redirecionar referências de associação de assembly para uma versão específica do .NET Estrutura. Esse atributo opcional usa um número de versão do .NET Framework para indicar qual versão aplica-se a. Se nenhum atributo **appliesTo** for especificado, o elemento [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) se aplica a todas as versões do .NET Framework.  
  
 Por exemplo, para redirecionar o assembly de associação para um assembly do .NET Framework 3.5, inclua o seguinte código XML no arquivo de configuração de aplicativo.  
  
```xml  
<runtime>  
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"   
    appliesTo="v3.5">  
    <dependentAssembly>   
      <!-- assembly information goes here -->  
    </dependentAssembly>  
  </assemblyBinding>  
</runtime>  
```  
  
 Você deve inserir as informações de redirecionamento em ordem de versão. Por exemplo, insira as informações de redirecionamento de associação de assembly para assemblies do .NET Framework 3.5 seguido de assemblies do .NET Framework 4.5. Por fim, insira as informações de redirecionamento de associação de assembly para qualquer redirecionamento de assembly do .NET Framework que não use o atributo **appliesTo** e, portanto, se aplica a todas as versões do .NET Framework. Se houver um conflito no redirecionamento, a primeira instrução de redirecionamento correspondente no arquivo de configuração é usada.  
  
 Por exemplo, para redirecionar uma referência a um assembly do .NET Framework 3.5 e outra referência a um assembly do .NET Framework 4, use o padrão mostrado no pseudocódigo a seguir.  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v3.5 ">   
  <!—.NET Framework version 3.5 redirects here -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v4.0.30319">   
  <!—.NET Framework version 4.0 redirects here -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
  <!-- redirects meant for all versions of the runtime -->   
</assemblyBinding>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Como habilitar e desabilitar o redirecionamento automático de associações](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [\<bindingRedirect > elemento](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [Permissão de segurança para redirecionamento de associações de assemblies](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)  
 [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Configurando aplicativos](../../../docs/framework/configure-apps/index.md)  
 [Configuração de aplicativos .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [Esquema de configurações do tempo de execução](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Como criar uma política de editor](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
