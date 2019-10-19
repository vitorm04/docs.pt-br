---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 3ee94df096b756be544964cfbbd405355e3f728f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581265"
---
# <a name="-delaysign"></a>-delaysign

Especifica se o assembly será assinado total ou parcialmente.

## <a name="syntax"></a>Sintaxe

```console
-delaysign[+ | -]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`  
Opcional. Use `-delaysign-` se você quiser um assembly totalmente assinado. Use `-delaysign+` se você quiser posicionar a chave pública no assembly e reservar espaço para o hash assinado. O padrão é `-delaysign-`.

## <a name="remarks"></a>Comentários

A opção `-delaysign` não tem nenhum efeito, a menos que seja usada com [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) ou [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).

Quando você solicita um assembly totalmente assinado, o compilador usa o hash no arquivo que contém o manifesto (metadados de assembly) e sinaliza esse hash com a chave particular. A assinatura digital resultante é armazenada no arquivo que contém o manifesto. Quando um assembly é assinado com atraso, o compilador não computa e armazena a assinatura, mas reserva espaço no arquivo para que a assinatura possa ser adicionada posteriormente.

Por exemplo, usando `-delaysign+`, um desenvolvedor em uma organização pode distribuir versões de teste não assinadas de um assembly que os testadores podem registrar com o cache de assembly global e usar. Quando o trabalho no assembly é concluído, a pessoa responsável pela chave privada da organização pode assinar totalmente o assembly. Essa compartimentalização protege a chave privada da organização contra a divulgação, ao mesmo tempo que permite que todos os desenvolvedores trabalhem nos assemblies.

Consulte [criando e usando assemblies de nome forte](../../../standard/assembly/create-use-strong-named.md) para obter mais informações sobre como assinar um assembly.

### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Para Set-delaysign no ambiente de desenvolvimento integrado do Visual Studio

1. Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.

2. Clique na guia **Assinatura**.

3. Defina o valor na caixa **somente assinatura de atraso** .

## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
