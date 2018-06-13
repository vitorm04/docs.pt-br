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
ms.openlocfilehash: 858ee30479c959f30673725b4ba8088fcc2d8f3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581749"
---
# <a name="security-and-user-input"></a>Segurança e entrada do usuário
Dados de usuário, que pode ser qualquer tipo de entrada (dados de uma solicitação da Web ou a URL de entrada para controles de um aplicativo do Microsoft Windows Forms e assim por diante), negativamente pode influenciar o código porque geralmente usados diretamente como parâmetros para chamar outro código. Essa situação é semelhante a chamar seu código com parâmetros estranhos um código mal-intencionado, e as mesmas precauções devem ser tomadas. Entrada do usuário é realmente difícil fazer seguro porque não há nenhum quadro de pilha para rastrear a presença de dados potencialmente não confiáveis.  
  
 Eles estão entre os bugs de segurança mais sutil e mais difícil localizar porque, embora eles podem existir em código aparentemente não relacionado à segurança, eles são um gateway para passar dados inválidos por meio de outro código. Para procurar por esses erros, execute qualquer tipo de dados de entrada, imagine que o intervalo de valores possíveis pode ser e considere se o código de ver esses dados pode lidar com todos os casos. Você pode corrigir esses erros por meio de intervalo de verificação e rejeitar qualquer entrada que o código não pode tratar.  
  
 Algumas considerações importantes que envolvem dados de usuário incluem o seguinte:  
  
-   Nenhum dado de usuário em uma resposta do servidor é executado no contexto do site do servidor no cliente. Se seu servidor Web usa dados de usuário e a insere na página da Web retornada, ele pode, por exemplo, incluir uma  **\<script >** marca e executar como se do servidor.  
  
-   Lembre-se de que o cliente pode solicitar qualquer URL.  
  
-   Considere os caminhos de difícil ou é inválidos:  
  
    -   .. \, caminhos extremamente longos.  
  
    -   Uso de caracteres curinga (*).  
  
    -   Expansão de token (% % de token).  
  
    -   Formulários estranhos dos caminhos com significado especial.  
  
    -   Alternativas de nomes de fluxo de sistema de arquivos, como `filename::$DATA`.  
  
    -   Abreviada versões dos nomes de arquivo, como `longfi~1` para `longfilename`.  
  
-   Lembre-se de que Eval(userdata) pode fazer nada.  
  
-   Tenha cuidado de associação tardia a um nome que inclui alguns dados do usuário.  
  
-   Se você estiver lidando com dados da Web, considere as várias formas de escapa é permitidas, incluindo:  
  
    -   Escapes hexadecimais (% nn).  
  
    -   Escapes de Unicode (% nnn).  
  
    -   Escapes de UTF-8 extensa (% nn % nn).  
  
    -   Escapes de duplos (% nn se torna mmnn %, onde % mm é o escape para '% s').  
  
-   Tenha cuidado dos nomes de usuário que podem ter mais de um formato canônico. Por exemplo, você pode usar o domínio de MYDOMAIN geralmente\\*username* formulário ou o *username* @mydomain.example.com formulário.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
