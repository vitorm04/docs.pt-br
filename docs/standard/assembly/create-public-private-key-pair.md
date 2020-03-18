---
title: Como criar um par de chaves pública/privada
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 8a9845e3cd18ff86ec04216ad0e9c5606186b113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73122528"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Como criar um par de chaves pública/privada

Para assinar um assembly com um nome forte, você deve ter um par de chaves pública/privada. Esse par de chaves de criptografia pública/privada é usado durante a compilação para criar um assembly de nome forte. Você pode criar um par de chaves usando a [ferramenta de Nome Forte (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md). Os arquivos do par de chaves geralmente têm uma extensão *.snk.*

> [!NOTE]
> No Visual Studio, as páginas de propriedade do projeto C# e Visual Basic incluem uma guia **de assinatura** que permite selecionar arquivos-chave existentes ou gerar novos arquivos-chave sem usar *o Sn.exe*. No Visual C++, você pode especificar o local de um arquivo de chave existente na página de propriedades **Avançado** na seção **Vinculador** da seção **Propriedades de Configuração** da janela **Páginas de Propriedades**. O uso <xref:System.Reflection.AssemblyKeyFileAttribute> do atributo para identificar pares de arquivos-chave tornou-se obsoleto a partir do Visual Studio 2005.

## <a name="create-a-key-pair"></a>Crie um par de chaves

Para criar um par de chaves, em um prompt de comando, digite o seguinte comando:

**sn –k** \<*nome de arquivo*>

Neste comando, *nome de arquivo* é o nome do arquivo de saída que contém o par de chaves.

O exemplo a seguir cria um par de chaves chamado *sgKey.snk*.

```cmd
sn -k sgKey.snk
```

Se você pretende atrasar a assinatura de um assembly e controla o par de chaves todo (o que é improvável fora de cenários de teste), pode usar os seguintes comandos para gerar um par de chaves e, em seguida, extrair a chave pública dele em um arquivo separado. Primeiro, crie o par de chaves:

```cmd
sn -k keypair.snk
```

Em seguida, extraia a chave pública do par de chaves e copie-a para um arquivo separado:

```cmd
sn -p keypair.snk public.snk
```

Depois de criar o par de chaves, você deve colocar o arquivo onde as ferramentas de assinatura de nome forte possam encontrá-lo.

Ao assinar um assembly com um nome forte, o [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) procura o arquivo de chave relativo ao diretório atual e ao diretório de saída. Ao usar compiladores de linha de comando, você pode simplesmente copiar a chave para o diretório atual que contém seus módulos de código.

Se você estiver usando uma versão anterior do Visual Studio que não tenha uma guia **Assinatura** nas propriedades do projeto, o local do arquivo de chave recomendado será o diretório do projeto com o atributo de arquivo especificado da seguinte maneira:

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a>Confira também

- [Criar e usar assemblies com nome forte](create-use-strong-named.md)
