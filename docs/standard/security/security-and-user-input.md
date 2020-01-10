---
title: Segurança e entrada do usuário
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: 0d34b06b44241feb7d6e3c8f76447b861563cfdc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705854"
---
# <a name="security-and-user-input"></a>Segurança e entrada do usuário

Os dados do usuário, que são qualquer tipo de entrada (dados de uma solicitação da Web ou URL, entrada para controles de um aplicativo Microsoft Windows Forms e assim por diante) podem influenciar o código de forma adversa, pois geralmente esses dados são usados diretamente como parâmetros para chamar outro código. Essa situação é análoga ao código mal-intencionado que chama seu código com parâmetros estranhos e as mesmas precauções devem ser tomadas. A entrada do usuário é realmente mais difícil de se tornar segura, pois não há um quadro de pilha para rastrear a presença dos dados potencialmente não confiáveis.

Esses são os bugs de segurança mais sutis e difíceis de serem encontrados porque, embora possam existir em código que pareça não estar relacionado à segurança, eles são um gateway para passar dados inválidos para outro código. Para procurar esses bugs, siga qualquer tipo de dado de entrada, imagine o que é o intervalo de possíveis valores e considere se o código que vê esses dados pode lidar com todos esses casos. Você pode corrigir esses bugs por meio da verificação de intervalo e rejeitar qualquer entrada que o código não possa manipular.

Algumas considerações importantes envolvendo os dados do usuário incluem o seguinte:

- Qualquer dado de usuário em uma resposta de servidor é executado no contexto do site do servidor no cliente. Se o seu servidor Web usa os dados do usuário e os insere na página da Web retornada, ele pode, por exemplo, incluir um **script de\<** marca e executar como se fosse no servidor.

- Lembre-se de que o cliente pode solicitar qualquer URL.

- Considere caminhos complicados ou inválidos:

  - .. \, caminhos extremamente longos.

  - Uso de caracteres curinga (*).

  - Expansão de token (% token%).

  - Formas estranhas de caminhos com significado especial.

  - Nomes de fluxo do sistema de arquivos alternativos, como `filename::$DATA`.

  - Versões curtas de nomes de arquivos, como `longfi~1` para `longfilename`.

- Lembre-se de que Eval (UserData) pode fazer qualquer coisa.

- Tenha cuidado com a associação tardia a um nome que inclua alguns dados do usuário.

- Se você estiver lidando com dados da Web, considere as várias formas de escapes que são permitidas, incluindo:

  - Escapes hexadecimais (% nn).

  - Escapes Unicode (% nnn).

  - Escapes UTF-8 longos (% nn% NN).

  - Escapes duplos (% nn torna-se% mmnn, em que% mm é o escape para '% ').

- Tenha cuidado com nomes de usuário que possam ter mais de um formato canônico. Por exemplo, geralmente você pode usar o formulário de nome de *usuário* de\\de domínio ou o *nome de usuário*@mydomain.example.com formulário.

## <a name="see-also"></a>Veja também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
