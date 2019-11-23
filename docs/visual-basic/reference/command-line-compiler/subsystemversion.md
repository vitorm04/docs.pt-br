---
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: a977bc4cff822de551bf82d0f31707e9b2b6ea41
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348532"
---
# <a name="-subsystemversion-visual-basic"></a>-subsystemversion (Visual Basic)

Especifica a versão mínima do subsistema no qual o arquivo executável gerado pode ser executado, determinando assim as versões do Windows em que o arquivo executável pode ser executado. Normalmente, essa opção garante que o arquivo executável possa tirar proveito de determinados recursos de segurança que não estão disponíveis com versões mais antigas do Windows.

> [!NOTE]
> Para especificar o subsistema em si, use a opção do compilador [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md).

## <a name="syntax"></a>Sintaxe

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a>Parâmetros

`major.minor`

A versão mínima obrigatória do subsistema, conforme expresso em uma notação de ponto para versões principais e secundárias. Por exemplo, você pode especificar que um aplicativo não pode ser executado em um sistema operacional mais antigo que o Windows 7 se definir o valor dessa opção como 6.01, conforme descrito na tabela mais adiante neste tópico. Você deve especificar os valores de `major` e `minor` como inteiros.

Zeros à esquerda na versão `minor` não alteram a versão, mas zeros à direita alteram. Por exemplo, 6.1 e 6.01 se referem à mesma versão, mas 6.10 se refere a uma versão diferente. É recomendável expressar a versão secundária como dois dígitos para evitar confusão.

## <a name="remarks"></a>Comentários

A seguinte tabela lista as versões de subsistema comuns do Windows.

|Versão do Windows|Versão do subsistema|
|---------------------|-----------------------|
|Windows 2000|5.00|
|Windows XP|5.01|
|Windows Server 2003|5.02|
|Windows Vista|6.00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|[!INCLUDE[win8](~/includes/win8-md.md)]|6.02|

## <a name="default-values"></a>Valores padrão

O valor padrão da opção do compilador **-subsystemversion** depende das condições na lista a seguir:

- O valor padrão é 6.02 se qualquer opção do compilador na lista a seguir for definida:

  - [/target:appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)

  - [/target:winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)

  - [-platform:arm](../../../visual-basic/reference/command-line-compiler/platform.md)

- O valor padrão será 6.00 se você estiver usando o MSBuild, se tiver como destino o .NET Framework 4.5 e se não definiu nenhuma das opções de compilador que foram especificadas anteriormente na lista.

- O valor padrão é 4.00 se nenhuma das condições anteriores for verdadeira.

## <a name="setting-this-option"></a>Definindo esta opção

To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML. Você não pode definir essa opção no IDE do Visual Studio. Para obter mais informações, consulte "Valores padrão" no início deste tópico ou [Propriedades de projeto comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)

- [Propriedades MSBuild](/visualstudio/msbuild/msbuild-properties)
