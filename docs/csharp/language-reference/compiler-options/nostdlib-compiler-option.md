---
title: -nostdlib (opções do compilador C#)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345085"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (opções do compilador C#)

**-nostdlib** impede a importação de mscorlib.dll, que define todo o namespace System.

## <a name="syntax"></a>Sintaxe

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Comentários

Use essa opção se desejar definir ou criar seus próprios objetos e namespace System.

Se você não especificar **-nostdlib**, o mscorlib.dll será importado no programa (o mesmo que especificar **-nostdlib-** ). Especificar **-nostdlib** é o mesmo que especificar **-nostdlib+** .

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para definir essa opção do compilador no Visual Studio

> [!NOTE]
> As instruções a seguir se aplicam apenas ao Visual Studio 2015 (e a versões anteriores). A propriedade de compilação **não referencia mscorlib. dll** não existe nas versões mais recentes do Visual Studio.

1. Abra a página **Propriedades** do projeto.

2. Clique na página de propriedades **Compilar**.

3. Clique no botão **Avançado**.

4. Modifique a propriedade **Não referenciar mscorlib.dll**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.

## <a name="see-also"></a>Veja também

- [Opções do compilador de C#](./index.md)
