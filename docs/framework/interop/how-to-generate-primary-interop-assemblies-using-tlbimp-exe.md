---
title: 'Como: Gerar assemblies de interoperabilidade primários usando Tlbimp.exe'
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fff2d3309e5f8872a9333bf3d2f86e52bd67ea5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971785"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Como: Gerar assemblies de interoperabilidade primários usando Tlbimp.exe

Há duas maneiras de gerar um assembly de interoperabilidade primário:

- Usando o [Importador de Biblioteca de Tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) fornecido pelo SDK do Windows.

  A maneira mais simples de gerar assemblies de interoperabilidade primários é usar o [Tlbimp.exe (Importador de Biblioteca de Tipos)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). O Tlbimp.exe fornece as seguintes garantias:

  - Verifica se há outros assemblies de interoperabilidade primários registrados antes de criar novos assemblies de interoperabilidade para quaisquer referências aninhadas de biblioteca de tipos.

  - Falhará ao emitir o assembly de interoperabilidade primário se você não especificar o contêiner ou o nome de arquivo para dar um nome forte ao assembly de interoperabilidade primário.

  - Falhará ao emitir um assembly de interoperabilidade primário se você omitir referências a assemblies dependentes.

  - Falhará ao emitir um assembly de interoperabilidade primário se você adicionar referências a assemblies dependentes que não forem assemblies de interoperabilidade primários.

- Criando assemblies de interoperabilidade primários manualmente no código-fonte usando uma linguagem em conformidade com CLS (Common Language Specification), tal como C#. Essa abordagem é útil quando uma biblioteca de tipos não está disponível.

Você deve ter um par de chaves de criptografia para assinar o assembly com um nome forte. Para obter detalhes, consulte [Criando um par de chaves](../../standard/assembly/create-public-private-key-pair.md).

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Para gerar um assembly de interoperabilidade primário usando Tlbimp.exe

1. No prompt de comando, digite:

    **tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*

    Neste comando, *tlbfile* é o arquivo que contém a biblioteca de tipo COM, *filename* é o nome do contêiner ou arquivo que contém o par de chaves e *assemblyname* é o nome do assembly a assinar com um nome forte.

Assemblies de interoperabilidade primários podem referenciar somente outros assemblies de interoperabilidade primários. Se seu assembly faz referência a tipos de uma biblioteca de tipos COM de terceiros, você deve obter um assembly de interoperabilidade primário do editor antes de gerar o assembly de interoperabilidade primário. Se você for o editor, você deverá gerar um assembly de interoperabilidade primário para a biblioteca de tipos dependentes antes de gerar o assembly de interoperabilidade primário que fará referência.

Um assembly de interoperabilidade primário dependente com um número de versão diferente daquele da biblioteca de tipos original não pode ser descoberto quando instalado no diretório atual. Você deverá registrar o assembly de interoperabilidade primário dependente no Registro do Windows ou usar a opção **/Reference** para certificar-se de que Tlbimp.exe localizará a DLL dependente.

Você também pode encapsular várias versões de uma biblioteca de tipos. Para obter instruções, veja [Como: Encapsular várias versões de bibliotecas de tipos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).

## <a name="example"></a>Exemplo

O exemplo a seguir importa a biblioteca de tipos COM `LibUtil.tlb` e assina o assembly `LibUtil.dll` com um nome forte usando o arquivo de chave `CompanyA.snk`. Omitindo um nome de namespace específico, este exemplo produz o namespace padrão, `LibUtil`.

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

Para um nome mais descritivo (usando a diretriz de nomenclatura *VendorName*.*LibraryName*), o exemplo a seguir substitui o nome do arquivo do assembly padrão e o nome do namespace.

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

O exemplo a seguir importa `MyLib.tlb`, que referencia `CompanyA.LibUtil.dll` e assina o assembly `CompanyB.MyLib.dll` com um nome forte usando o arquivo de chave `CompanyB.snk`. O namespace `CompanyB.MyLib` substitui o nome do namespace padrão.

```console
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a>Consulte também

- [Como: Registrar assemblies de interoperabilidade primários](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
