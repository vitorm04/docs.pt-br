---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d093b8ce4413a375e79eec239be37e83ac674d05
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417643"
---
# <a name="-errorreport"></a>-errorreport

Especifica como o compilador do Visual Basic deve relatar erros internos do compilador.

## <a name="syntax"></a>Sintaxe

```
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a>Comentários

Essa opção fornece uma maneira conveniente de relatar um erro interno do compilador do Visual Basic (ICE) para a equipe do Visual Basic na Microsoft. Por padrão, o compilador não envia informações à Microsoft. No entanto, se você encontrar um erro interno do compilador, esta opção permite que você relate o erro à Microsoft. Essas informações ajudam os engenheiros da Microsoft a identificar a causa e podem ajudar a melhorar a próxima versão do Visual Basic.

Capacidade de um usuário de enviar relatórios depende de permissões de política de computador e de usuário.

A tabela a seguir resume o efeito do `-errorreport` opção.

|Opção|Comportamento|
|---|---|
|`prompt`|Se ocorrer um erro interno do compilador, uma caixa de diálogo aparece para que você possa exibir os dados exatos que o compilador coletado. Você pode determinar se há informações confidenciais no relatório de erros e tomar uma decisão sobre se deseja enviá-lo à Microsoft. Se você optar por enviá-lo, e as configurações de política de computador e usuário permitirem, o compilador envia os dados à Microsoft.|
|`queue`|Enfileira o relatório de erros. Ao fazer logon com privilégios de administrador, você pode relatar quaisquer falhas desde a última vez em que você estava conectado (você não precisará enviar relatórios de falhas mais de uma vez a cada três dias). Esse é o comportamento padrão quando o `-errorreport` opção não for especificada.|
|`send`|Se ocorrer um erro interno do compilador, e as configurações de política de computador e usuário permitirem, o compilador envia os dados à Microsoft.<br /><br /> A opção `-errorreport:send` tenta enviar informações de erro à Microsoft automaticamente se o relatório está habilitado pela [relatório de erros do Windows](/windows/desktop/wer/windows-error-reporting) configurações do sistema. |
|`none`|Se ocorrer um erro interno do compilador, ele será não ser coletado ou enviado à Microsoft.|

O compilador envia os dados que incluem a pilha no momento do erro, que geralmente inclui algum código-fonte. Se `-errorreport` é usado com o [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, em seguida, o arquivo de origem inteiro é enviado.

Essa opção é melhor usada com o [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) opção, pois permite que os engenheiros da Microsoft mais facilmente reproduzir o erro.

> [!NOTE]
> O `-errorreport` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.

## <a name="example"></a>Exemplo

O código a seguir tenta compilar `T2.vb`, e se o compilador encontra um erro interno do compilador, ele solicitará que você enviar o relatório de erros à Microsoft.

```
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
