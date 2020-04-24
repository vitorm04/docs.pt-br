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
ms.openlocfilehash: 0d55171e37ec056b3470d238a60bc32f2feb04fb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646037"
---
# <a name="redirecting-assembly-versions"></a>Redirecionando versões de assembly

Você pode redirecionar referências de vinculação em tempo de compilação para conjuntos de framework .NET, assembléias de terceiros ou conjuntos de seu próprio aplicativo. Você pode redirecionar seu aplicativo para usar uma versão diferente de um conjunto de várias maneiras: através da política do publisher, através de um arquivo de configuração de aplicativo; ou através do arquivo de configuração da máquina. Este artigo discute como a vinculação de montagem funciona no Quadro .NET e como ela pode ser configurada.

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a>Unificação da montagem e vinculação padrão
 As vinculações às assembléias do Quadro .NET às vezes são redirecionadas através de um processo chamado *unificação de montagem*. O .NET Framework consiste em uma versão do tempo de execução do idioma comum e cerca de duas dúzias de conjuntos .NET Framework que compõem a biblioteca do tipo. Essas assembléias do Quadro .NET são tratadas pelo tempo de execução como uma única unidade. Por padrão, quando um aplicativo é lançado, todas as referências a tipos em código executados pelo tempo de execução são direcionadas para conjuntos .NET Framework que têm o mesmo número de versão que o tempo de execução que é carregado em um processo. Os redirecionamentos que ocorrem com este modelo são o comportamento padrão para o tempo de execução.

 Por exemplo, se o aplicativo faz referência a tipos no namespace System.XML e foi construído usando o .NET Framework 4.5, ele contém referências estáticas ao conjunto System.XML que é fornecido com a versão 4.5 em tempo de execução. Se você quiser redirecionar a referência de vinculação para apontar para o conjunto System.XML que é enviado com o .NET Framework 4, você pode colocar informações de redirecionamento no arquivo de configuração do aplicativo. Um redirecionamento vinculativo em um arquivo de configuração para um conjunto .NET Framework unificado cancela a unificação para essa montagem.

 Além disso, você pode querer redirecionar manualmente a vinculação de montagem para conjuntos de terceiros se houver várias versões disponíveis.

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a>Redirecionando versões de montagem usando a política do editor
 Os fornecedores de assembléias podem direcionar aplicativos para uma versão mais recente de um conjunto, incluindo um arquivo de política de editorcom o novo conjunto. O arquivo de diretiva do editor, localizado no cache global de montagem, contém configurações de redirecionamento de montagem.

 Cada *major.* *versão menor* de uma montagem tem seu próprio arquivo de diretiva de editor. Por exemplo, os redirecionamentos da versão 2.0.2.222 para 2.0.3.000 e da versão 2.0.2.321 para a versão 2.0.3.000 vão para o mesmo arquivo, porque estão associados à versão 2.0. No entanto, um redirecionamento da versão 3.0.0.999 para a versão 4.0.0.000 vai para o arquivo para a versão 3.0.999. Cada versão principal do .NET Framework tem seu próprio arquivo de diretiva de editor.

 Se existir um arquivo de diretiva de editor para um conjunto, o tempo de execução verificará este arquivo após verificar o arquivo de configuração do manifesto e do aplicativo da assembléia. Os fornecedores devem usar arquivos de diretiva de editor somente quando o novo conjunto for compatível com o conjunto que está sendo redirecionado.

 Você pode ignorar a política do editor para o seu aplicativo especificando configurações no arquivo de configuração do aplicativo, conforme discutido na [seção 'Ignorar diretiva do editor'.](#bypass_PP)

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a>Redirecionando versões de montagem no nível do aplicativo
 Existem algumas técnicas diferentes para alterar o comportamento vinculante do seu aplicativo através do arquivo de configuração do aplicativo: você pode editar manualmente o arquivo, pode confiar no redirecionamento de vinculação automática ou pode especificar o comportamento vinculante ignorando a política do editor.

### <a name="manually-editing-the-app-config-file"></a>Editando manualmente o arquivo de configuração do aplicativo
 Você pode editar manualmente o arquivo de configuração do aplicativo para resolver problemas de montagem. Por exemplo, se um fornecedor pode liberar uma versão mais recente de um conjunto que seu aplicativo usa sem fornecer uma política de editor, porque eles não garantem compatibilidade retrógrada, você pode direcionar seu aplicativo para usar a versão mais recente do conjunto colocando informações de vinculação de montagem no arquivo de configuração do aplicativo da seguinte forma.

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a>Contando com o redirecionamento automático da ligação

Quando você cria um aplicativo de desktop no Visual Studio que tem como alvo o .NET Framework 4.5.1 ou uma versão posterior, o aplicativo usa redirecionamento de vinculação automática. Isso significa que, se dois componentes referenciarem versões diferentes do mesmo conjunto com nome forte, o tempo de execução automaticamente adicionará um redirecionamento vinculativo à versão mais recente do conjunto na configuração do aplicativo de saída (app.config). Esse redirecionamento substitui a unificação da assembléia que poderia ocorrer de outra forma. O arquivo de origem app.config não é modificado. Por exemplo, digamos que seu aplicativo faça referência direta a um componente .NET Framework de banda, mas usa uma biblioteca de terceiros que tem como alvo uma versão mais antiga do mesmo componente. Quando você compila o aplicativo, o arquivo de configuração do aplicativo de saída é modificado para conter um redirecionamento vinculativo para a versão mais recente do componente. Se você criar um aplicativo web, você receberá um aviso de compilação sobre o conflito de vinculação, que, por sua vez, lhe dá a opção de adicionar o redirecionamento de vinculação necessário ao arquivo de configuração da Web de origem.

Se você adicionar manualmente redirecionamentos de vinculação ao arquivo source app.config, no momento da compilação, o Visual Studio tentará unificar os conjuntos com base nos redirecionamentos de vinculação adicionados. Por exemplo, digamos que você insira o seguinte redirecionamento de vinculação para uma montagem:

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

Se outro projeto no aplicativo fizer referência à versão 1.0.0.0 do mesmo conjunto, o redirecionamento de vinculação automática adicionará a seguinte entrada ao arquivo output app.config para que o aplicativo seja unificado na versão 2.0.0.0 deste conjunto:

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

Você pode habilitar o redirecionamento de vinculação automática se o aplicativo tiver como alvo versões mais antigas do .NET Framework. Você pode substituir esse comportamento padrão fornecendo informações de redirecionamento vinculante no arquivo app.config para qualquer montagem ou desligando o recurso de redirecionamento de vinculação. Para obter informações sobre como ativar ou desativar esse recurso, consulte Como: Ativar e desativar o [redirecionamento automático de vinculação](how-to-enable-and-disable-automatic-binding-redirection.md).

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a>Ignorando a política do editor
 Você pode substituir a política do editor no arquivo de configuração do aplicativo, se necessário. Por exemplo, novas versões de conjuntos que afirmam ser compatíveis com o retrocesso ainda podem quebrar um aplicativo. Se você quiser ignorar a [ \<](./file-schema/runtime/publisherpolicy-element.md) política do editor, adicione um elemento de>de **apply** de editor ao **yes** [ \<](./file-schema/runtime/dependentassembly-element.md) elemento dependentAssembly>no arquivo de configuração do aplicativo e defina o atributo de aplicação como **não,** o que substitui quaisquer configurações yes anteriores.

 `<publisherPolicy apply="no" />`

 Contorne a política do editor para manter seu aplicativo funcionando para seus usuários, mas certifique-se de relatar o problema ao fornecedor de montagem. Se um conjunto tiver um arquivo de diretiva de editor, o fornecedor deve certificar-se de que o conjunto é compatível com o atraso e que os clientes podem usar a nova versão o máximo possível.

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a>Redirecionando versões de montagem no nível da máquina
 Pode haver casos raros quando um administrador de máquinas quer que todos os aplicativos em um computador usem uma versão específica de um conjunto. Por exemplo, o administrador pode querer que cada aplicativo use uma versão de montagem específica, porque essa versão corrige uma falha de segurança. Se um conjunto for redirecionado no arquivo de configuração da máquina, todos os aplicativos dessa máquina que usam a versão antiga serão direcionados para usar a nova versão. O arquivo de configuração da máquina substitui o arquivo de configuração do aplicativo e o arquivo de diretiva do editor. Esse arquivo está localizado no diretório %*runtime install path*%\Config. Normalmente, o .NET Framework está instalado no diretório %drive%\Windows\Microsoft.NET\Framework.

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a>Especificando a vinculação do conjunto em arquivos de configuração
 Você usa o mesmo formato XML para especificar redirecionamentos de vinculação, seja no arquivo de configuração do aplicativo, no arquivo de configuração da máquina ou no arquivo de diretiva do editor. Para redirecionar uma versão de montagem para outra, use o [ \<elemento vinculaçãoRedirecionar>.](./file-schema/runtime/bindingredirect-element.md) O atributo **oldVersion** pode especificar uma única versão de montagem ou uma série de versões. O `newVersion` atributo deve especificar uma única versão.  Por exemplo, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` especifica que o tempo de execução deve usar a versão 2.0.0.0 em vez das versões de montagem entre 1.1.0.0 e 1.2.0.0.

 O exemplo de código a seguir demonstra uma variedade de cenários de redirecionamento vinculante. O exemplo especifica um redirecionamento para `myAssembly`uma gama de versões para , e um único redirecionamento de vinculação para `mySecondAssembly`. O exemplo também especifica que o arquivo de diretiva do `myThirdAssembly`editor não substituirá os redirecionamentos de vinculação para .

 Para vincular um conjunto, você deve especificar a string "urn:schemas-microsoft-com:asm.v1" com o atributo **xmlns** na tag [ \<assemblyBinding>.](./file-schema/runtime/assemblybinding-element-for-runtime.md)

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

### <a name="limiting-assembly--bindings-to-a-specific-version"></a>Limitando as vinculações de montagem a uma versão específica
 Você pode usar o atributo **appliesTo** no [ \<elemento assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) em um arquivo de configuração de aplicativo para redirecionar referências de vinculação de montagem para uma versão específica do .NET Framework. Este atributo opcional usa um número de versão .NET Framework para indicar a qual versão ele se aplica. Se nenhum atributo **appliesTo** for especificado, o elemento [\<assemblyBinding>](./file-schema/runtime/assemblybinding-element-for-runtime.md) se aplica a todas as versões do .NET Framework.

 Por exemplo, para redirecionar a vinculação de montagem para um conjunto .NET Framework 3.5, você incluiria o seguinte código XML no arquivo de configuração do aplicativo.

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

 Você deve inserir informações de redirecionamento na ordem de versão. Por exemplo, insira informações de redirecionamento de vinculação de montagem para conjuntos .NET Framework 3.5 seguidos de conjuntos .NET Framework 4.5. Por fim, insira as informações de redirecionamento de associação de assembly para qualquer redirecionamento de assembly do .NET Framework que não use o atributo **appliesTo** e, portanto, se aplica a todas as versões do .NET Framework. Se houver um conflito no redirecionamento, a primeira instrução de redirecionamento correspondente no arquivo de configuração será usada.

 Por exemplo, para redirecionar uma referência a um conjunto .NET Framework 3.5 e outra a um conjunto .NET Framework 4, use o padrão mostrado no seguinte pseudocódigo.

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!--.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!--.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a>Confira também

- [Como habilitar e desabilitar o redirecionamento automático de associações](how-to-enable-and-disable-automatic-binding-redirection.md)
- [\<vinculaçãoRedirecionar> Elemento](./file-schema/runtime/bindingredirect-element.md)
- [Permissão de segurança para redirecionamento de associações de assemblies](assembly-binding-redirection-security-permission.md)
- [Assemblies no .NET](../../standard/assembly/index.md)
- [Programação com assemblies](../../standard/assembly/index.md)
- [Como o runtime localiza assemblies](../deployment/how-the-runtime-locates-assemblies.md)
- [Configurando aplicativos](index.md)
- [Esquema de configurações em tempo de execução](./file-schema/runtime/index.md)
- [Esquema de arquivo de configuração](./file-schema/index.md)
- [Como criar uma política de editor](how-to-create-a-publisher-policy.md)
