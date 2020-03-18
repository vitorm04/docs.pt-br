---
title: Segurança e entrada do usuário
description: Seu código pode passar dados inseridos pelo usuário como parâmetros para outro código, o que pode afetar a segurança. Você pode fazer verificação de intervalo para rejeitar entrada problemática.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: fa9f8d4708e928c51e446d8369c9b4556fc6fb77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186103"
---
# <a name="security-and-user-input"></a>Segurança e entrada do usuário

Os dados do usuário, que é qualquer tipo de entrada (dados de uma solicitação da Web ou URL, entrada para controles de um aplicativo Microsoft Windows Forms, e assim por diante), podem influenciar negativamente o código porque muitas vezes esses dados são usados diretamente como parâmetros para chamar outro código. Esta situação é análoga ao código malicioso chamando seu código com parâmetros estranhos, e as mesmas precauções devem ser tomadas. A entrada do usuário é realmente mais difícil de tornar segura porque não há um quadro de pilha para rastrear a presença dos dados potencialmente não confiáveis.

Estes estão entre os bugs de segurança mais sutis e difíceis de encontrar porque, embora possam existir em códigos aparentemente não relacionados à segurança, eles são uma porta de entrada para passar dados ruins para outro código. Para procurar esses bugs, siga qualquer tipo de dados de entrada, imagine qual seria o alcance dos valores possíveis e considere se o código que vê esses dados pode lidar com todos esses casos. Você pode corrigir esses bugs através da verificação de alcance e rejeitando qualquer entrada que o código não possa lidar.

Algumas considerações importantes envolvendo dados do usuário incluem:

- Qualquer dado de usuário em uma resposta de servidor é executado no contexto do site do servidor no cliente. Se o servidor da Web pega os dados do usuário e os insere na página da Web retornada, ele pode, por exemplo, incluir um ** \<script>** tag e executado como se fosse do servidor.

- Lembre-se que o cliente pode solicitar qualquer URL.

- Considere caminhos complicados ou inválidos:

  - .. \ , caminhos extremamente longos.

  - Uso de caracteres curinga (*).

  - Expansão do token (%token%).

  - Estranhas formas de caminhos com significado especial.

  - Nomes de fluxo de `filename::$DATA`sistema de arquivos alternativos, tais como .

  - Versões curtas de `longfi~1` `longfilename`nomes de arquivos, como para .

- Lembre-se que Eval (userdata) pode fazer qualquer coisa.

- Tenha cuidado com a vinculação tardia a um nome que inclua alguns dados do usuário.

- Se você está lidando com dados da Web, considere as várias formas de fugas que são permitidas, incluindo:

  - Fugas hexadecimais (%nn).

  - Fugas unicode (%nnn).

  - Fugas de UTF-8 long overlong (%nn%nn).

  - Fugas duplas (%nn torna-se %mmnn, onde %mm é a fuga para '%').

- Desconfie de nomes de usuários que possam ter mais de um formato canônico. Por exemplo, muitas vezes você\\pode usar o formulário*mydomain username* ou o formulário *de nome de* @mydomain.example.com usuário.

## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
