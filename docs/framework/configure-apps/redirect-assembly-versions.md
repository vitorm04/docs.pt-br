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
ms.openlocfilehash: 060f2bfdc39e7fe4ab0a28a4aecec87db89d3428
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46705647"
---
# <a name="redirecting-assembly-versions"></a>Redirecionando versões de assembly

Você pode redirecionar referências de associação de tempo de compilação para assemblies do .NET Framework, assemblies de terceiros ou assemblies do seu próprio aplicativo. Você pode redirecionar seu aplicativo para usar uma versão diferente de um assembly de várias maneiras: por meio da política de publicador, por meio de um arquivo de configuração do aplicativo; ou por meio do arquivo de configuração do computador. Este artigo discute como a associação de assembly funciona no .NET Framework e como ele pode ser configurado.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Unificação do assembly e associação padrão
 Associações de assemblies do .NET Framework são redirecionadas às vezes por meio de um processo chamado *Unificação do assembly*. O .NET Framework consiste em uma versão do common language runtime e aproximadamente duas dúzias assemblies do .NET Framework que compõem a biblioteca de tipos. Esses assemblies do .NET Framework são tratados pelo tempo de execução como uma única unidade. Por padrão, quando um aplicativo é iniciado, todas as referências a tipos no código executado pelo tempo de execução são direcionadas para os assemblies do .NET Framework que têm o mesmo número de versão que o tempo de execução que é carregado em um processo. As reorientações que ocorrem com esse modelo são o comportamento padrão para o tempo de execução.

 Por exemplo, se seu aplicativo faz referência a tipos no namespace System. XML e foi criado usando o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ele contém referências estáticas ao assembly System. XML que é fornecido com a versão de tempo de execução 4.5. Se você deseja redirecionar a referência de associação para apontar para o assembly System. XML que vêm com o .NET Framework 4, você pode colocar informações de redirecionamento no arquivo de configuração do aplicativo. Um redirecionamento de associação em um arquivo de configuração para um assembly unificado do .NET Framework cancela a Unificação para aquele assembly.

 Além disso, você talvez queira redirecionar manualmente a associação de assembly para assemblies de terceiros se houver várias versões disponíveis.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Redirecionando versões de assembly por meio da política de publicador
 Os fornecedores de assemblies podem direcionar aplicativos para uma versão mais recente de um assembly, incluindo um arquivo de política do publicador com o novo assembly. O arquivo de política de publicador, que está localizado no cache de assembly global, contém as configurações de redirecionamento do assembly.

 Cada *principais*. *pequenas* versão de um assembly tem seu próprio arquivo de política do publicador. Por exemplo, os redirecionamentos da versão 2.0.2.222 a 2.0.3.000 e da versão 2.0.2.321 a versão 2.0.3.000 ambos ir no mesmo arquivo, porque eles estão associados com a versão 2.0. No entanto, um redirecionamento da versão 3.0.0.999 para a versão 4.0.0.000 entra no arquivo da versão 3.0.999. Cada versão principal do .NET Framework tem seu próprio arquivo de política de editor.

 Se existir um arquivo de política de publicador para um assembly, o runtime verifica esse arquivo depois de verificar se o arquivo de configuração de aplicativo e manifesto do assembly. Os fornecedores devem usar arquivos de política de editor somente quando o novo assembly é compatível com versões anteriores com o assembly que está sendo redirecionado.

 Você pode ignorar a política de publicador para seu aplicativo especificando as configurações no arquivo de configuração do aplicativo, conforme discutido na [ignorando seção de política de publicador](#bypass_PP).

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Redirecionando versões de assembly no nível do aplicativo
 Existem algumas técnicas diferentes para alterar o comportamento de associação para seu aplicativo por meio do arquivo de configuração de aplicativo: você pode editar manualmente o arquivo, você pode confiar no redirecionamento de associação automática ou você pode especificar o comportamento de associação ignorando a política de editor.

### <a name="manually-editing-the-app-config-file"></a>Editando manualmente o arquivo de configuração de aplicativo
 Você pode editar manualmente o arquivo de configuração de aplicativo para resolver problemas do assembly. Por exemplo, se um fornecedor pode liberar uma versão mais recente de um assembly que seu aplicativo usa sem fornecer uma política de editor, porque eles não garantem a compatibilidade com versões anteriores, você pode direcionar seu aplicativo para usar a versão mais recente do assembly, colocando o assembly associando informações no arquivo de configuração do seu aplicativo da seguinte maneira.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Depender de redirecionamento de associação automática

Quando você cria um aplicativo da área de trabalho no Visual Studio que tem como alvo o [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] ou uma versão posterior, o aplicativo usa o redirecionamento de associação automática. Isso significa que se dois componentes fizerem referência a versões diferentes do mesmo assembly de nome forte, o runtime adiciona automaticamente um redirecionamento de associação para a versão mais recente do assembly no arquivo de configuração (App. config) do aplicativo de saída. Esta redirecionamento substitui a Unificação do assembly que pode ocorrer de outra forma. O arquivo de origem app.config não é modificado. Por exemplo, digamos que seu aplicativo diretamente referencia um componente do .NET Framework fora de banda, mas usa uma biblioteca de terceiros que tem como alvo uma versão mais antiga do mesmo componente. Quando você compila o aplicativo, o arquivo de configuração de aplicativo de saída é modificado para conter um redirecionamento de associação para a versão mais recente do componente. Se você criar um aplicativo web, você receberá um aviso de compilação sobre o conflito de associação, que por sua vez, oferece a opção para adicionar o redirecionamento de associação necessários para o arquivo de configuração da web de origem.

Se você adicionar manualmente redirecionamentos de ligação ao arquivo App. config de origem, em tempo de compilação, o Visual Studio tentará unificar os assemblies com base nos redirecionamentos de associação que você adicionou. Por exemplo, digamos que você insere o seguinte redirecionamento de associação para um assembly:

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Se a versão 1.0.0.0 do mesmo assembly faz referência a outro projeto em seu aplicativo, o redirecionamento de associação automática adiciona a seguinte entrada ao arquivo de saída de App. config para que o aplicativo seja unificado na versão 2.0.0.0 desse assembly:

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Você pode habilitar o redirecionamento de associação automático se seu aplicativo tem como alvo as versões mais antigas do .NET Framework. Você pode substituir esse comportamento padrão, fornecendo informações de redirecionamento de associação no arquivo App. config para qualquer assembly ou desativando o recurso de redirecionamento de associação. Para obter informações sobre como ativar ou desativar a esse recurso, consulte [como: habilitar e desabilitar o redirecionamento automático de associações](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Ignorar políticas de editor
 Você pode substituir a política de editor no arquivo de configuração do aplicativo, se necessário. Por exemplo, as novas versões dos assemblies que alegam ser compatíveis com versões anteriores ainda podem interromper um aplicativo. Se você quiser ignorar a política de editor, adicione uma [ \<publisherPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elemento para o [ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) elemento no arquivo de configuração de aplicativo e defina o **se aplicam** atributo **nenhuma**, que substitui qualquer anterior **Sim** configurações.

 `<publisherPolicy apply="no" />`

 Ignorar a política de editor para manter seu aplicativo em execução para seus usuários, mas certifique-se de que relatar o problema ao fornecedor do assembly. Se um assembly tiver um arquivo de política de editor, o fornecedor assegure-se de que o assembly é compatível com versões anteriores e que os clientes podem usar a nova versão tanto quanto possível.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Redirecionando versões de assembly no nível do computador
 Pode haver casos raros quando um administrador do computador deseja todos os aplicativos em um computador para usar uma versão específica de um assembly. Por exemplo, o administrador pode desejar que cada aplicativo para usar uma versão específica do assembly, porque essa versão corrige um buraco de segurança. Se um assembly for redirecionado no arquivo de configuração do computador, todos os aplicativos nessa máquina que usam a versão antiga serão direcionados para usar a nova versão. O arquivo de configuração do computador substitui o arquivo de configuração de aplicativo e o arquivo de política do publicador. Esse arquivo está localizado no diretório %*runtime install path*%\Config. Normalmente, o .NET Framework é instalado no diretório %drive%\Windows\Microsoft.NET\Framework directory.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Especificando arquivos de configuração de associação de assembly
 Você pode usar o mesmo formato XML para especificar os redirecionamentos de associação, seja no arquivo de configuração de aplicativo, o arquivo de configuração do computador ou o arquivo de política do publicador. Para redirecionar uma versão do assembly para outra, use o [ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md) elemento. O **oldVersion** atributo pode especificar uma única versão do assembly ou um intervalo de versões. O `newVersion` atributo deve especificar uma única versão.  Por exemplo, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` Especifica que o tempo de execução deve usar a versão 2.0.0.0 em vez das versões de assembly entre 1.1.0.0 e 1.2.0.0.

 O exemplo de código a seguir demonstra uma variedade de cenários de redirecionamento de associação. O exemplo especifica um redirecionamento para um intervalo de versões para `myAssembly`e uma única associação é redirecionada para `mySecondAssembly`. O exemplo também especifica esse arquivo de política do publicador não substituirá os redirecionamentos de associação para `myThirdAssembly`.

 Para associar a um assembly, você deve especificar a cadeia de caracteres "urn: schemas-microsoft-v1" com o **xmlns** atributo na [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) marca.

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

### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Limitando associações de assembly para uma versão específica
 Você pode usar o **appliesTo** atributo as [ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) elemento em um arquivo de configuração de aplicativo para redirecionar referências de associação de assembly para uma versão específica do .NET Estrutura. Esse atributo opcional usa um número de versão do .NET Framework para indicar qual versão ele se aplica ao. Se nenhum atributo **appliesTo** for especificado, o elemento [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) se aplica a todas as versões do .NET Framework.

 Por exemplo, para redirecionar a associação de assembly para um assembly do .NET Framework 3.5, você incluiria o seguinte código XML no arquivo de configuração de aplicativo.

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

 Você deve inserir informações de redirecionamento na ordem de versão. Por exemplo, insira as informações de redirecionamento de associação de assembly para assemblies do .NET Framework 3.5 seguidos por assemblies do .NET Framework 4.5. Por fim, insira as informações de redirecionamento de associação de assembly para qualquer redirecionamento de assembly do .NET Framework que não use o atributo **appliesTo** e, portanto, se aplica a todas as versões do .NET Framework. Se houver um conflito no redirecionamento, a primeira instrução de redirecionamento correspondente no arquivo de configuração é usada.

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

- [Como habilitar e desabilitar o redirecionamento automático de associações](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<bindingRedirect > elemento](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [Permissão de segurança para redirecionamento de associações de assemblies](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)
- [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Configurando aplicativos](../../../docs/framework/configure-apps/index.md)
- [Configuração de aplicativos .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
- [Esquema de configurações do tempo de execução](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md)
- [Como criar uma política de editor](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
