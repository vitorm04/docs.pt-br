---
title: 'Como: Assinar um assembly com um nome forte'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 527fd68ef40e152b57a1fc98113094d3b41fbaae
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973057"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Como: Assinar um assembly com um nome forte

> [!NOTE]
> Embora o .NET Core dê suporte a assemblies de nome forte e todos os assemblies na biblioteca do .NET Core sejam assinados, a maioria dos assemblies de terceiros não precisa de nomes fortes. Para obter mais informações, consulte [assinatura de nome forte](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md) no github.

Há vários modos de assinar um assembly com um nome forte:  
  
- Usando a guia **Assinatura** na caixa de diálogo **Propriedades** de um projeto no Visual Studio. Esta é a forma mais fácil e conveniente de assinar um assembly com um nome forte.  
  
- Usando o [vinculador do assembly (al. exe)](../../framework/tools/al-exe-assembly-linker.md) para vincular um módulo de código de .NET Framework (um arquivo *. netmodule* ) a um arquivo de chave.  
  
- Usando atributos de assembly para inserir as informações do nome forte no seu código. Você pode usar o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute>, dependendo do local em que o arquivo de chave a ser usado se encontra.  
  
- Usando opções do compilador.  
  
 Você deve ter um par de chaves de criptografia para assinar um assembly com um nome forte. Para obter mais informações de como criar um par de chaves, confira [Como Como criar um par de chaves pública/privada](create-public-private-key-pair.md).  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Criar e assinar um assembly com um nome forte usando o Visual Studio  
  
1. No **Gerenciador de Soluções**, abra o menu de atalho do projeto e, em seguida, escolha **Propriedades**.  
  
2. Escolha a guia **Assinatura**.  
  
3. Marque a caixa **Assinar o assembly**.  
  
4. Na caixa **escolher um arquivo de chave de nome forte** , escolha **procurar**e, em seguida, navegue até o arquivo de chave. Para criar um novo arquivo de chave, escolha **novo** e digite seu nome na caixa de diálogo **criar chave de nome forte** .  
  
> [!NOTE]
> Para [assinar um assembly com atraso](delay-sign.md), escolha um arquivo de chave pública.  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Criar e assinar um assembly com um nome forte usando o vinculador de assembly  
  
No [prompt de comando do desenvolvedor para o Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), digite o seguinte comando:  

**al** **/out:** \<*assemblyName*>  *\<moduleName>* **/keyfile:** \<*keyfileName*>  

Sendo que:  

- *AssemblyName* é o nome do assembly com assinatura forte (um arquivo *. dll* ou *. exe* ) que o vinculador de assembly emitirá.  
  
- *ModuleName* é o nome de um módulo de código .NET Framework (um arquivo *. netmodule* ) que inclui um ou mais tipos. Você pode criar um arquivo *. netmodule* compilando seu código com o `/target:module` switch in C# ou Visual Basic.
  
- *fileFileName* é o nome do contêiner ou arquivo que contém o par de chaves. O vinculador de assembly interpreta um caminho relativo em relação ao diretório atual.  

O exemplo a seguir assina o assembly *myAssembly. dll* com um nome forte usando o arquivo de chave *sgKey. SNK*.  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
Para saber mais sobre essa ferramenta, veja [Vinculador de Assembly](../../framework/tools/al-exe-assembly-linker.md).  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Assinar um assembly com um nome forte usando atributos  
  
1. Adicione o atributo <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> ao seu arquivo de código-fonte e especifique o nome do arquivo ou contêiner que contém o par de chaves a ser usado ao assinar o assembly com um nome forte.  
   
2. Compile o arquivo de código-fonte normalmente.  
   
   > [!NOTE]
   > Os compiladores de C# e Visual Basic emitem avisos do compilador (CS1699 e BC41008, respectivamente) quando encontram o atributo <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> no código-fonte. Você pode ignorar os avisos.  

O exemplo a seguir usa <xref:System.Reflection.AssemblyKeyFileAttribute> o atributo com um arquivo de chave chamado *keyfile. SNK*, que está localizado no diretório em que o assembly é compilado.  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

Você também pode atrasar a assinatura de um assembly ao compilar seu arquivo de código-fonte. Para obter mais informações, veja [assinar um assembly com atraso](delay-sign.md).  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Assinar um assembly com um nome forte usando o compilador  

Compile seu arquivo ou arquivos de código-fonte com a opção de compilador `/keyfile` ou `/delaysign` no C# e em Visual Basic, ou a opção de vinculador `/KEYFILE` ou `/DELAYSIGN` em C++. Depois do nome da opção, adicione um dois-pontos e o nome do arquivo da chave. Ao usar compiladores de linha de comando, você pode copiar o arquivo de chave para o diretório que contém seus arquivos de código-fonte.  

Para obter informações sobre assinatura de atraso, consulte [assinar um assembly com atraso](delay-sign.md).  

O exemplo a seguir usa C# o compilador e assina o assembly *UtilityLibrary. dll* com um nome forte usando o arquivo de chave *sgKey. SNK*.  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a>Consulte também

- [Criar e usar assemblies de nome forte](create-use-strong-named.md)
- [Como: Criar um par de chaves pública/privada](create-public-private-key-pair.md)
- [Al.exe (Assembly Linker)](../../framework/tools/al-exe-assembly-linker.md)
- [Assinar um assembly com atraso](delay-sign.md)
- [Gerenciar assinatura de assembly e de manifesto](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [Página de assinatura, Designer de Projeto](/visualstudio/ide/reference/signing-page-project-designer)
