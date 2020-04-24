---
title: Como criar uma política de editor
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646056"
---
# <a name="how-to-create-a-publisher-policy"></a>Como criar uma política de editor

Os fornecedores de assembléias podem afirmar que os aplicativos devem usar uma versão mais recente de um conjunto, incluindo um arquivo de diretiva de editor com o conjunto atualizado. O arquivo de diretiva do editor especifica o redirecionamento de montagem e as configurações de base de código e usa o mesmo formato de um arquivo de configuração de aplicativo. O arquivo de diretiva do editor é compilado em uma montagem e colocado no cache de montagem global.

Existem três etapas envolvidas na criação de uma política de editores:

1. Crie um arquivo de política de editor.

2. Crie uma montagem de política de editores.

3. Adicione a montagem da diretiva do editor ao cache de montagem global.

O esquema para a política do editor é descrito no [Redirecionamento de Versões de Montagem](redirect-assembly-versions.md). O exemplo a seguir mostra um arquivo de `myAssembly` diretiva de editor que redireciona uma versão para outra.

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

Para saber como especificar uma base de código, consulte [Especificando a localização de um conjunto](specify-assembly-location.md).

## <a name="creating-the-publisher-policy-assembly"></a>Criando a Assembléia de Políticas de Editores

Use o [Linker de montagem (Al.exe)](../tools/al-exe-assembly-linker.md) para criar a montagem da diretiva do editor.

#### <a name="to-create-a-publisher-policy-assembly"></a>Para criar uma montagem de política de editores

Digite o seguinte comando no prompt de comando:

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

Neste comando:

- O `publisherPolicyFile` argumento é o nome do arquivo de política do editor.

- O `publisherPolicyAssemblyFile` argumento é o nome da assembléia de política do editor que resulta deste comando. O nome do arquivo de montagem deve seguir o formato:

  'policy.majorNumber.minorNumber.mainAssemblyName.dll'

- O `keyPairFile` argumento é o nome do arquivo que contém o par de chaves. Você deve assinar a montagem e a montagem da política do editor com o mesmo par de chaves.

- O `processorArchitecture` argumento identifica a plataforma direcionada por um conjunto específico do processador.

  > [!NOTE]
  > A capacidade de segmentar uma arquitetura específica de processador está disponível a partir do .NET Framework 2.0.

A capacidade de segmentar uma arquitetura específica de processador está disponível a partir do .NET Framework 2.0. O comando a seguir cria `policy.1.0.myAssembly` uma montagem de `pub.config`diretiva de editor chamada a partir de `sgKey.snk` um arquivo de diretiva de editor chamado, atribui um nome forte ao conjunto usando o par de chaves no arquivo e especifica que o conjunto tem como alvo a arquitetura do processador x86.

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

A montagem da diretiva do editor deve corresponder à arquitetura do processador do conjunto a que se aplica. Assim, se a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> sua <xref:System.Reflection.ProcessorArchitecture.MSIL>montagem tiver um valor de , a `/platform:anycpu`montagem da política do editor para essa montagem deve ser criada com . Você deve fornecer uma montagem de diretiva de editor separada para cada conjunto específico do processador.

Uma conseqüência desta regra é que, para alterar a arquitetura do processador para um conjunto, você deve alterar o componente principal ou menor do número da versão, para que você possa fornecer um novo conjunto de políticas de editor com a arquitetura correta do processador. A antiga montagem de diretiva de editor não pode atender seu conjunto uma vez que seu conjunto tenha uma arquitetura de processador diferente.

Outra conseqüência é que o linker versão 2.0 não pode ser usado para criar um conjunto de políticas de editorpara um conjunto compilado usando versões anteriores do .NET Framework, porque ele sempre especifica a arquitetura do processador.

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Adicionando a Assembléia de Políticas de Editores ao Cache de Montagem Global

Use a [ferramenta Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) para adicionar a montagem da diretiva do editor ao cache de montagem global.

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Para adicionar a montagem da diretiva do editor ao cache de montagem global

Digite o seguinte comando no prompt de comando:

```console
gacutil /i publisherPolicyAssemblyFile
```

O comando `policy.1.0.myAssembly.dll` a seguir adiciona-se ao cache de montagem global.

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> A montagem da diretiva do editor não pode ser adicionada ao `/link` cache de montagem global, a menos que o arquivo de diretiva de editor original especificado no argumento esteja localizado no mesmo diretório da montagem.

## <a name="see-also"></a>Confira também

- [Programação com assemblies](../../standard/assembly/index.md)
- [Como o runtime localiza assemblies](../deployment/how-the-runtime-locates-assemblies.md)
- [Configurando aplicativos usando arquivos de configuração ](index.md)
- [Esquema de configurações em tempo de execução](./file-schema/runtime/index.md)
- [Esquema de arquivo de configuração](./file-schema/index.md)
- [Redirecionando versões de assembly](redirect-assembly-versions.md)
