---
title: -publicsign (opções do compilador C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 01ce30b9ac5997f56f29dcbbfa43a27738fa5556
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43474246"
---
# <a name="-publicsign-c-compiler-options"></a>-publicsign (opções do compilador C#)

Essa opção faz com que o compilador aplique uma chave pública, mas, na verdade, não assina o assembly. A opção **-publicsign** também define um bit no assembly que informa o tempo de execução que o arquivo realmente já está assinado.

## <a name="syntax"></a>Sintaxe

```console
-publicsign
```

## <a name="arguments"></a>Arguments

nenhuma.

## <a name="remarks"></a>Comentários

A opção **-publicsign** requer o uso de [-keyfile](keyfile-compiler-option.md) ou [-keycontainer](keycontainer-compiler-option.md). As opções **keyfile** ou **keycontainer** especificam a chave pública.

As opções **-publicsign** e **-delaysign** são mutuamente exclusivas.

Às vezes chamada de "assinatura falsa" ou "assinatura de OSS", a assinatura pública inclui a chave pública em um assembly de saída e define o sinalizador "assinado", mas, na verdade, não assina o assembly com uma chave privada. Isso é útil para projetos de software livre em que as pessoas desejam criar assemblies compatíveis com os assemblies "totalmente assinados" lançados, mas não têm acesso à chave privada usada para assinar os assemblies. Como quase nenhum consumidor precisa verificar realmente se o assembly está totalmente assinado, esses assemblies criados publicamente podem ser usados em quase todos os cenários nos quais o assembly totalmente assinado seria usado.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a página **Propriedades** do projeto.
1. Modifique a propriedade **Apenas adiar a assinatura**.

## <a name="see-also"></a>Consulte também

- [Opção -delaysign do compilador C#](delaysign-compiler-option.md)  
- [Opção -keyfile do compilador C#](keyfile-compiler-option.md)  
- [Opção -keycontainer do compilador C#](keycontainer-compiler-option.md)  
- [Opções do compilador de C#](index.md)  
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
