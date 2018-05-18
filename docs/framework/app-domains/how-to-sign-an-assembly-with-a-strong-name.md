---
title: Como assinar um assembly com um nome forte
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45f8ad3bd9226ffd821fc792cdd4d0a6dac1a414
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Como assinar um assembly com um nome forte
Há vários modos de assinar um assembly com um nome forte:  
  
-   Usando a guia **Assinatura** na caixa de diálogo **Propriedades** de um projeto no Visual Studio. Esta é a forma mais fácil e conveniente de assinar um assembly com um nome forte.  
  
-   Usando o [Vinculador de Assembly (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) para vincular um módulo de código do .NET Framework (um arquivo .netmodule) com um arquivo de chave.  
  
-   Usando atributos de assembly para inserir as informações do nome forte no seu código. Você pode usar o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute>, dependendo do local em que o arquivo de chave a ser usado se encontra.  
  
-   Usando opções do compilador.  
  
 Você deve ter um par de chaves de criptografia para assinar um assembly com um nome forte. Para saber mais sobre como criar um par de chaves, veja [Como criar um par de chaves pública-privada](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Para criar e assinar um assembly com um nome forte usando o Visual Studio.  
  
1.  No **Gerenciador de Soluções**, abra o menu de atalho do projeto e, em seguida, escolha **Propriedades**.  
  
2.  Escolha a guia **Assinatura**.  
  
3.  Marque a caixa **Assinar o assembly**.  
  
4.  Na caixa **Escolher um arquivo de chave com nome forte**, selecione **\<Procurar…>** e, em seguida, navegue até o arquivo de chave. Para criar um novo arquivo de chave, selecione **\<Novo…>** e digite o nome na caixa de diálogo **Criar Chave de Nome Forte**.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Para criar e assinar um assembly com um nome forte usando o Vinculador de Assembly.  
  
-   No [prompt de comando do Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), digite o seguinte comando:  
  
     **al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*>  
  
     em que:  
  
     *assemblyName*  
     O nome forte do assembly assinado (um arquivo .dll ou .exe) que o Vinculador de Assembly emitirá.  
  
     *moduleName*  
     O nome de um módulo de código do .NET Framework (um arquivo .netmodule) que inclui um ou mais tipos. Você pode criar um arquivo .netmodule ao compilar seu código com a opção `/target:module` em C# ou no Visual Basic.  
  
     *keyfileName*  
     O nome do contêiner ou arquivo que contém o par de chaves. O Vinculador de Assembly interpreta um caminho relativo em relação ao diretório atual.  
  
 O exemplo a seguir assina o assembly `MyAssembly.dll` com um nome forte usando o arquivo de chave `sgKey.snk`.  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 Para saber mais sobre essa ferramenta, veja [Vinculador de Assembly](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Para assinar um assembly com um nome forte usando atributos  
  
1.  Adicione o atributo <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> ao seu arquivo de código-fonte e especifique o nome do arquivo ou contêiner que contém o par de chaves a ser usado ao assinar o assembly com um nome forte.  
  
2.  Compile o arquivo de código-fonte normalmente.  
  
> [!NOTE]
>  Os compiladores de C# e Visual Basic emitem avisos do compilador (CS1699 e BC41008, respectivamente) quando encontram o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> no código-fonte. Você pode ignorar os avisos.  
  
 O exemplo de código a seguir usa o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> com um arquivo de chave chamado `keyfile.snk`, localizado no diretório onde o assembly é compilado.  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 Você também pode atrasar a assinatura de um assembly ao compilar seu arquivo de código-fonte. Para obter mais informações, consulte [Assinando um assembly com atraso](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Para assinar um assembly com um nome forte usando o compilador  
  
-   Compile seu arquivo ou arquivos de código-fonte com a opção de compilador `/keyfile` ou `/delaysign` no C# e em Visual Basic, ou a opção de vinculador `/KEYFILE` ou `/DELAYSIGN` em C++. Depois do nome da opção, adicione um dois-pontos e o nome do arquivo da chave. Ao usar compiladores de linha de comando, você pode copiar o arquivo de chave para o diretório que contém seus arquivos de código-fonte.  
  
     Para saber mais sobre assinatura com atraso, veja [Assinar um assembly com atraso](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
     O exemplo a seguir usa o compilador C# e assina o assembly `UtilityLibrary.dll` com um nome forte usando o arquivo de chave `sgKey.snk`.  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Criar e usar assemblies de nomes fortes](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Como criar um par de chaves pública/privada](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Assinar um assembly com atraso](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [Gerenciando Assinatura de Assembly e Manifesto](/visualstudio/ide/managing-assembly-and-manifest-signing)  
 [Página de Assinatura, Designer de Projeto](https://msdn.microsoft.com/library/0k50fs3b)
