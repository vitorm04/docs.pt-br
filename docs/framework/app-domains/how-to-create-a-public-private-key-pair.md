---
title: 'Como: Criar um par de chaves pública/privada'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71eaaa85b8bd287c37f59116e75cf99b030d63ac
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297831"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Como: Criar um par de chaves pública/privada

Para assinar um assembly com um nome forte, você deve ter um par de chaves pública/privada. Esse par de chaves de criptografia pública/privada é usado durante a compilação para criar um assembly de nome forte. Você pode criar um par de chaves usando a [ferramenta de Nome Forte (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md). Os arquivos de par de chaves geralmente têm uma extensão .snk.

> [!NOTE]
> No Visual Studio, as páginas de propriedades de projeto C# e Visual Basic incluem uma guia **Assinatura** que permite que você selecione arquivos de chave existentes ou gere novos arquivos de chaves sem usar Sn.exe. No Visual C++, você pode especificar o local de um arquivo de chave existente na página de propriedades **Avançado** na seção **Vinculador** da seção **Propriedades de Configuração** da janela **Páginas de Propriedades**. O uso do atributo <xref:System.Reflection.AssemblyKeyFileAttribute> para identificar pares de arquivos de chave se tornou obsoleto a partir do Visual Studio 2005.

## <a name="to-create-a-key-pair"></a>Para criar um par de chaves

1. No prompt de comando, digite o seguinte comando:

     **sn –k** \<*nome de arquivo*>

     Neste comando, *nome de arquivo* é o nome do arquivo de saída que contém o par de chaves.

 O exemplo a seguir cria um par de chaves chamado `sgKey.snk`.

```
sn -k sgKey.snk
```

 Se você pretende atrasar a assinatura de um assembly e controla o par de chaves todo (o que é improvável fora de cenários de teste), pode usar os seguintes comandos para gerar um par de chaves e, em seguida, extrair a chave pública dele em um arquivo separado. Primeiro, crie o par de chaves:

```
sn -k keypair.snk
```

 Em seguida, extraia a chave pública do par de chaves e copie-a para um arquivo separado:

```
sn -p keypair.snk public.snk
```

 Depois de criar o par de chaves, você deve colocar o arquivo onde as ferramentas de assinatura de nome forte possam encontrá-lo.

 Ao assinar um assembly com um nome forte, o [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) procura o arquivo de chave relativo ao diretório atual e ao diretório de saída. Ao usar compiladores de linha de comando, você pode simplesmente copiar a chave para o diretório atual que contém seus módulos de código.

 Se você estiver usando uma versão anterior do Visual Studio que não tenha uma guia **Assinatura** nas propriedades do projeto, o local do arquivo de chave recomendado será o diretório do projeto com o atributo de arquivo especificado da seguinte maneira:

 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]

## <a name="see-also"></a>Consulte também

- [Criando e usando assemblies de nomes fortes](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
