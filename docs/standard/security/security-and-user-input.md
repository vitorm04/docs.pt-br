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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27818d5e1779cd6e10e11830f91a20a3e638639a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933777"
---
# <a name="security-and-user-input"></a>Segurança e entrada do usuário
Dados de usuário, que é qualquer tipo de entrada (dados de uma solicitação da Web ou URL de entrada para controles de um aplicativo do Microsoft Windows Forms e assim por diante), negativamente pode influenciar o código porque frequentemente esses dados são usados diretamente como parâmetros para chamar outro código. Essa situação é análoga ao código malicioso chame seu código com parâmetros estranhos e as mesmas precauções devem ser tomadas. Entrada do usuário é, na verdade, mais difícil tornar segura porque não há nenhum quadro de pilha para rastrear a presença de dados potencialmente não confiáveis.  
  
 Eles estão entre os bugs de segurança mais sutil e mais difíceis de localizar porque, embora eles podem existir em código aparentemente não relacionado à segurança, eles são um gateway para passar dados inválidos por meio de outro código. Para procurar esses bugs, siga qualquer tipo de dados de entrada, imagine o que o intervalo de valores possíveis pode ser e considere se o código vendo esses dados pode lidar com todos esses casos. Você pode corrigir esses bugs por meio do intervalo de verificação e rejeitar qualquer entrada que o código não pode manipular.  
  
 Algumas considerações importantes que envolvem dados de usuário incluem o seguinte:  
  
- Qualquer dado de usuário em uma resposta do servidor é executado no contexto do site do servidor no cliente. Se seu servidor Web usa dados de usuário e o insere na página da Web retornada, ele pode, por exemplo, incluir um  **\<script >** de marca e executar como se do servidor.  
  
- Lembre-se de que o cliente pode solicitar qualquer URL.  
  
- Considere caminhos complicados ou é inválidos:  
  
    - .. \, caminhos extremamente longos.  
  
    - Uso de caracteres curinga (*).  
  
    - Expansão de token (% % token).  
  
    - Formulários estranhos dos caminhos com significado especial.  
  
    - Alternativa de nomes de fluxo de sistema de arquivos, como `filename::$DATA`.  
  
    - Curto versões dos nomes de arquivo, como `longfi~1` para `longfilename`.  
  
- Lembre-se de que Eval(userdata) pode fazer qualquer coisa.  
  
- Tenha cuidado de associação tardia a um nome que inclui alguns dados do usuário.  
  
- Se você estiver lidando com dados da Web, considere as diversas formas de escape que é permitido, incluindo:  
  
    - Escapa hexadecimal (% nn).  
  
    - Escapes de Unicode (% nnn).  
  
    - Escapa extensa de UTF-8 (% nn % nn).  
  
    - Escapes de duplos (% nn se torna mmnn %, onde % mm é o escape para '% s').  
  
- Esteja atento a nomes de usuário que podem ter mais de um formato canônico. Por exemplo, você geralmente pode usar ambos o MYDOMAIN\\*nome de usuário* formulário ou o *username* @mydomain.example.com formulário.  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
