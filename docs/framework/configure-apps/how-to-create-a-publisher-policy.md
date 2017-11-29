---
title: "Como criar uma política de editor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 430426e3662582bd904bc088a362e9d7ed331c11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-publisher-policy"></a>Como criar uma política de editor
Fornecedores de módulos (assemblies) podem indicar que os aplicativos devem usar uma versão mais recente de um assembly, incluindo um arquivo de política do publicador com o assembly atualizado. O arquivo de política de publicador Especifica as configurações de base de código e redirecionamento de assembly e usa o mesmo formato, como um arquivo de configuração do aplicativo. O arquivo de política de publicador é compilado em um assembly e colocado no cache de assembly global.  
  
 Há três etapas envolvidas na criação de uma política de editor:  
  
1.  Crie um arquivo de política do publicador.  
  
2.  Crie um assembly de política do publicador.  
  
3.  Adicione o assembly de política do publicador no cache de assembly global.  
  
 O esquema para a política de editor é descrito em [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md). O exemplo a seguir mostra um editor de arquivo de política que redireciona uma versão do `myAssembly` para outro.  
  
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
  
 Para saber como especificar uma base de código, consulte [especificando o local de um Assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).  
  
## <a name="creating-the-publisher-policy-assembly"></a>Criar o Assembly de política do publicador  
 Use o [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) para criar o assembly de política do publicador.  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>Para criar um assembly de política do publicador  
  
1.  Digite o seguinte comando no prompt de comando:  
  
     **Al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:**  *keyPairFile* **/platform:** *processorArchitecture*  
  
     Este comando:  
  
    -   O *publisherPolicyFile* argumento é o nome do arquivo de diretiva publisher.  
  
    -   O *publisherPolicyAssemblyFile* argumento é o nome do assembly da diretiva publisher resultados deste comando. O nome do arquivo assembly deve seguir o formato:  
  
         **diretiva.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **. dll**  
  
    -   O *keyPairFile* argumento é o nome do arquivo que contém o par de chaves. Você deve assinar o assembly e o assembly de política do publicador com o mesmo par de chaves.  
  
    -   O *processorArchitecture* argumento identifica a plataforma de destino por um assembly de processador específico.  
  
        > [!NOTE]
        >  A capacidade de uma arquitetura de processador específico de destino é nova no .NET Framework versão 2.0.  
  
     O comando a seguir cria um assembly de diretiva publisher chamado `policy.1.0.myAssembly` de um arquivo de política de publicador chamado `pub.config`, atribui um nome forte ao assembly usando o par de chaves no `sgKey.snk` de arquivos e especifica que o assembly tem como alvo o x86 arquitetura do processador.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     O assembly da diretiva publisher deve corresponder à arquitetura de processador do assembly que ele se aplica ao. Assim, se seu assembly tem um <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> valor <xref:System.Reflection.ProcessorArchitecture.MSIL>, o assembly de política de publicador para esse assembly deve ser criado com `/platform:anycpu`. Você deve fornecer um separado assembly de política de publicador para cada assembly específicas do processador.  
  
     Uma consequência dessa regra é que, para alterar a arquitetura do processador para um assembly, você deve alterar o componente principal ou secundário do número de versão, para que você pode fornecer um novo assembly de política do publicador com a arquitetura de processador correta. O assembly antigo da diretiva publisher não pode atender seu assembly quando seu assembly tem uma arquitetura de processador diferente.  
  
     Outra consequência é que o vinculador versão 2.0 não pode ser usado para criar um assembly de política do publicador para um assembly compilado usando versões anteriores do .NET Framework, porque ela sempre Especifica a arquitetura do processador.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Adicionar o Assembly de política do publicador no cache de Assembly Global  
 Use o [ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) para adicionar o assembly de política do publicador no cache de assembly global.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Para adicionar o assembly de política do publicador no cache de assembly global  
  
1.  Digite o seguinte comando no prompt de comando:  
  
     **gacutil /i***publisherPolicyAssemblyFile*   
  
     O comando a seguir adiciona `policy.1.0.myAssembly.dll` ao cache de assembly global.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  O assembly da diretiva publisher não pode ser adicionado ao cache de assembly global, a menos que o arquivo de política do publicador original está localizado no mesmo diretório que o assembly.  
  
## <a name="see-also"></a>Consulte também  
 [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Configurando aplicativos](../../../docs/framework/configure-apps/index.md)  
 [Configuração de aplicativos .NET Framework](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [Esquema de configurações do tempo de execução](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Redirecionando versões de assembly](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
