---
title: 'Como: Criar uma política de editor'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: bf5b55eb01a31106fcc7cb0d79212416ab0c898d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913053"
---
# <a name="how-to-create-a-publisher-policy"></a>Como: Criar uma política de editor
Os fornecedores de assemblies podem declarar que os aplicativos devem usar uma versão mais recente de um assembly, incluindo um arquivo de política do Publicador com o assembly atualizado. O arquivo de política do Publicador especifica as configurações de redirecionamento de assembly e base de código e usa o mesmo formato que um arquivo de configuração de aplicativo. O arquivo de política do Publicador é compilado em um assembly e colocado no cache de assembly global.  
  
 Há três etapas envolvidas na criação de uma política de editor:  
  
1. Crie um arquivo de política do Publicador.  
  
2. Crie um assembly de política do Publicador.  
  
3. Adicione o assembly de política do Publicador ao cache de assembly global.  
  
 O esquema para a política do Publicador é descrito em redirecionar [versões de assembly](redirect-assembly-versions.md). O exemplo a seguir mostra um arquivo de política do Publicador que redireciona uma `myAssembly` versão do para outra.  
  
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
  
 Para saber como especificar uma base de código, consulte [especificando o local de um assembly](specify-assembly-location.md).  
  
## <a name="creating-the-publisher-policy-assembly"></a>Criando o assembly de política do Publicador  
 Use o [vinculador de assembly (al. exe)](../tools/al-exe-assembly-linker.md) para criar o assembly de política do Publicador.  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>Para criar um assembly de política do Publicador  
  
1. Digite o seguinte comando no prompt de comando:  
  
     **Al/link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *par de chaves* **/Platform:** *ProcessorArchitecture*  
  
     Neste comando:  
  
    - O argumento *publisherPolicyFile* é o nome do arquivo de política do Publicador.  
  
    - O argumento *publisherPolicyAssemblyFile* é o nome do assembly de política do Publicador que resulta desse comando. O nome do arquivo de assembly deve seguir o formato:  
  
         **policy.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    - O argumento keyparfile é o nome do arquivo que contém o par de chaves. Você deve assinar o assembly e o assembly da política do Publicador com o mesmo par de chaves.  
  
    - O argumento *ProcessorArchitecture* identifica a plataforma de destino de um assembly específico do processador.  
  
        > [!NOTE]
        >  A capacidade de direcionar uma arquitetura de processador específica é nova na versão .NET Framework 2,0.  
  
     O comando a seguir cria um assembly de política `policy.1.0.myAssembly` do publicador chamado de um `pub.config`arquivo de política do publicador chamado, atribui um nome forte ao assembly usando `sgKey.snk` o par de chaves no arquivo e especifica que o assembly tem como alvo o x86 arquitetura do processador.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     O assembly de política do Publicador deve corresponder à arquitetura de processador do assembly ao qual ele se aplica. Portanto, se o assembly tiver um <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> valor de <xref:System.Reflection.ProcessorArchitecture.MSIL>, o assembly de política de editor para esse assembly deverá ser `/platform:anycpu`criado com. Você deve fornecer um assembly de política de Publicador separado para cada assembly específico de processador.  
  
     Uma consequência dessa regra é que, para alterar a arquitetura do processador de um assembly, você deve alterar o componente principal ou secundário do número de versão, para que você possa fornecer um novo assembly de política de Publicador com a arquitetura de processador correta. O antigo assembly de política do Publicador não pode atender ao seu assembly depois que o assembly tem uma arquitetura de processador diferente.  
  
     Outra consequência é que o vinculador da versão 2,0 não pode ser usado para criar um assembly de política do Publicador para um assembly compilado usando versões anteriores do .NET Framework, porque ele sempre especifica a arquitetura do processador.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Adicionando o assembly de política do Publicador ao cache de assembly global  
 Use a [ferramenta global assembly cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) para adicionar o assembly de política do Publicador ao cache de assembly global.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Para adicionar o assembly de política do Publicador ao cache de assembly global  
  
1. Digite o seguinte comando no prompt de comando:  
  
     **gacutil /i**  *publisherPolicyAssemblyFile*  
  
     O comando a seguir `policy.1.0.myAssembly.dll` adiciona ao cache de assembly global.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  O assembly de política do Publicador não pode ser adicionado ao cache de assembly global, a menos que o arquivo de política original do Publicador esteja localizado no mesmo diretório que o assembly.  
  
## <a name="see-also"></a>Consulte também

- [Programação com assemblies](../app-domains/programming-with-assemblies.md)
- [Como o tempo de execução localiza assemblies](../deployment/how-the-runtime-locates-assemblies.md)
- [Configurando aplicativos usando arquivos de configuração](index.md)
- [Esquema de configurações do tempo de execução](./file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](./file-schema/index.md)
- [Redirecionando versões de assembly](redirect-assembly-versions.md)
