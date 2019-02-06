---
title: 'Como: Criar uma política de editor'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: b98d3ef62fc9dda48920d32fed6f6acf797334d6
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758983"
---
# <a name="how-to-create-a-publisher-policy"></a>Como: Criar uma política de editor
Os fornecedores de assemblies podem declarar que os aplicativos devem usar uma versão mais recente de um assembly, incluindo um arquivo de política do publicador com o assembly atualizado. O arquivo de política de publicador Especifica as configurações de base de código e redirecionamento de assembly e usa o mesmo formato que o arquivo de configuração do aplicativo. O arquivo de política de publicador é compilado em um assembly e colocado no cache de assembly global.  
  
 Há três etapas envolvidas na criação de uma política de editor:  
  
1.  Crie um arquivo de política do publicador.  
  
2.  Crie um assembly de política do publicador.  
  
3.  Adicione o assembly de política do publicador para o cache de assembly global.  
  
 O esquema para a política de editor é descrito na [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md). O exemplo a seguir mostra um editor de arquivo de política que redireciona uma versão do `myAssembly` para outro.  
  
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
  
 Para saber como especificar uma base de código, consulte [especificando o local do Assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).  
  
## <a name="creating-the-publisher-policy-assembly"></a>Criar o Assembly de política do publicador  
 Use o [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) para criar o assembly de política do publicador.  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>Para criar um assembly de política do publicador  
  
1.  Digite o seguinte comando no prompt de comando:  
  
     **al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*  
  
     Neste comando:  
  
    -   O *publisherPolicyFile* argumento é o nome do arquivo de política de publicador.  
  
    -   O *publisherPolicyAssemblyFile* argumento é o nome do assembly da diretiva de editor que é o resultado desse comando. O nome de arquivo do assembly deve seguir o formato:  
  
         **policy.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   O *keyPairFile* argumento é o nome do arquivo que contém o par de chaves. Você deve assinar o assembly e o assembly de política do publicador com o mesmo par de chaves.  
  
    -   O *processorArchitecture* argumento identifica a plataforma de destino por um assembly específico do processador.  
  
        > [!NOTE]
        >  A capacidade de direcionar uma arquitetura de processador específico é nova no .NET Framework versão 2.0.  
  
     O comando a seguir cria um assembly de política de publicador chamado `policy.1.0.myAssembly` de um arquivo de política de publicador chamado `pub.config`, atribui um nome forte ao assembly usando o par de chaves no `sgKey.snk` de arquivo e especifica que o assembly é destinado a x86 arquitetura do processador.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     O assembly de política do publicador deve corresponder à arquitetura do processador do assembly que ele se aplica ao. Portanto, se seu assembly tiver um <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> valor de <xref:System.Reflection.ProcessorArchitecture.MSIL>, o assembly de política de publicador para esse assembly deve ser criado com `/platform:anycpu`. Você deve fornecer um separado assembly de política de publicador para cada assembly específico do processador.  
  
     Uma consequência dessa regra é que, para alterar a arquitetura do processador para um assembly, você deve alterar o componente principal ou secundário do número de versão, para que você pode fornecer um novo assembly de política do publicador com a arquitetura de processador correta. O assembly de política de publicador antigo não pode atender a seu assembly depois que o assembly tem uma arquitetura de processador diferente.  
  
     Outra consequência é que o vinculador versão 2.0 não pode ser usado para criar um assembly de política de publicador para um assembly compilado usando versões anteriores do .NET Framework, pois ele sempre Especifica a arquitetura do processador.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Adicionando o Assembly de política do publicador para o Cache de Assembly Global  
 Use o [ferramenta de Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) para adicionar o assembly de política de publicador para o cache de assembly global.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Para adicionar o assembly de política de publicador para o cache de assembly global  
  
1.  Digite o seguinte comando no prompt de comando:  
  
     **gacutil /i**  *publisherPolicyAssemblyFile*  
  
     O comando a seguir adiciona `policy.1.0.myAssembly.dll` ao cache de assembly global.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  O assembly de política do publicador não pode ser adicionado ao cache de assembly global, a menos que o arquivo de política do publicador original está localizado no mesmo diretório que o assembly.  
  
## <a name="see-also"></a>Consulte também
- [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Configurando aplicativos usando arquivos de configuração](../../../docs/framework/configure-apps/index.md)
- [Esquema de configurações do tempo de execução](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md)
- [Redirecionando versões de assembly](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
