---
title: Validação de complexidade de senhas (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdbe5f385c6b7a0898c4907b0d8afabdaed06fa0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>Instruções passo a passo: validando senhas complexas (Visual Basic)
Este método verifica se há algumas características de senha forte e atualiza um parâmetro de cadeia de caracteres com informações sobre quais verifica a senha falha.  
  
 Senhas podem ser usadas em um sistema seguro para autorizar um usuário. No entanto, as senhas devem ser difícil para usuários não autorizados estimem. Os invasores podem usar um *ataque de dicionário* programa que itera por meio de todas as palavras de um dicionário (ou vários dicionários em idiomas diferentes) e teste se alguma das palavras funciona como uma senha de usuário. Senhas fracas como "Yankees" ou "Mustang" podem ser adivinhadas rapidamente. Senhas de alto nível, como "? Você 'L1N3vaFiNdMeyeP@sSWerd! ", são muito menos prováveis de ser adivinhada. Um sistema protegido por senha deve garantir que os usuários escolham senhas fortes.  
  
 Uma senha forte é complexa (que contém uma mistura de caracteres maiusculo, minúsculo, numérico e especial) e não é uma palavra. Este exemplo demonstra como verificar a complexidade.  
  
## <a name="example"></a>Exemplo  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Chame este método passando a cadeia de caracteres que contém a senha.  
  
 Este exemplo requer:  
  
-   Acesso aos membros do namespace <xref:System.Text.RegularExpressions>. Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código. Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Segurança  
 Se você estiver movendo a senha em uma rede, você precisa usar um método seguro de transferência de dados. Para obter mais informações, consulte [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).  
  
 Você pode melhorar a precisão do `ValidatePassword` função adicionando verificações de complexidade adicional:  
  
-   Compare a senha e suas substrings com o nome do usuário, o identificador de usuário e um dicionário definido pelo aplicativo. Além disso, trate caracteres visualmente similares como equivalentes ao executar as comparações. Por exemplo, trate as letras "l" e "e" como equivalentes aos numerais "1" e "3".  
  
-   Se houver apenas um caractere maiusculo, certifique-se de não é o primeiro caractere do password.  
  
-   Certifique-se de que os dois últimos caracteres da senha são letras.  
  
-   Não permita senhas em que todos os símbolos são inseridos na linha superior do teclado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Text.RegularExpressions.Regex>  
 [Segurança de aplicativo Web ASP .NET](https://msdn.microsoft.com/library/330a99hc)
