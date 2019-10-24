---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: a9741f7a8283f8603e02dae5abea151c6ee5d75e
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775663"
---
# <a name="-errorreport"></a>-errorreport

Especifica como o compilador de Visual Basic deve relatar erros internos do compilador.

## <a name="syntax"></a>Sintaxe

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a>Comentários

Essa opção fornece uma maneira conveniente de relatar um erro de compilador interno do Visual Basic (ICE) para a equipe de Visual Basic da Microsoft. Por padrão, o compilador não envia informações à Microsoft. No entanto, se você encontrar um erro interno do compilador, essa opção permitirá que você relate o erro à Microsoft. Essas informações ajudarão os engenheiros da Microsoft a identificar a causa e podem ajudar a melhorar a próxima versão do Visual Basic.

A capacidade do usuário de enviar relatórios depende das permissões de política de computador e de usuário.

A tabela a seguir resume o efeito da opção `-errorreport`.

|Opção|Comportamento|
|---|---|
|`prompt`|Se ocorrer um erro de compilador interno, uma caixa de diálogo aparecerá para que você possa exibir os dados exatos que o compilador coletou. Você pode determinar se há alguma informação confidencial no relatório de erros e tomar uma decisão sobre se deseja enviá-la à Microsoft. Se você decidir enviá-lo e as configurações de política de computador e de usuário permitirem, o compilador enviará os dados para a Microsoft.|
|`queue`|Enfileira o relatório de erros. Ao fazer logon com privilégios de administrador, você pode relatar quaisquer falhas desde a última vez que você fez logon (não será solicitado que você envie relatórios para falhas mais de uma vez a cada três dias). Esse é o comportamento padrão quando a opção `-errorreport` não é especificada.|
|`send`|Se ocorrer um erro de compilador interno e as configurações de política de computador e de usuário permitirem, o compilador enviará os dados para a Microsoft.<br /><br /> A opção `-errorreport:send` tenta enviar informações de erro automaticamente para a Microsoft se o relatório estiver habilitado pelas configurações do sistema [relatório de erros do Windows](/windows/desktop/wer/windows-error-reporting) . |
|`none`|Se ocorrer um erro interno do compilador, ele não será coletado nem enviado à Microsoft.|

O compilador envia dados que incluem a pilha no momento do erro, que geralmente inclui um código-fonte. Se `-errorreport` for usado com a opção [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) , o arquivo de origem inteiro será enviado.

Essa opção é melhor usada com a opção [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) , pois permite que os engenheiros da Microsoft reproduzam o erro mais facilmente.

> [!NOTE]
> A opção `-errorreport` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.

## <a name="example"></a>Exemplo

O código a seguir tenta compilar `T2.vb` e, se o compilador encontrar um erro de compilador interno, ele solicitará que você envie o relatório de erros à Microsoft.

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
