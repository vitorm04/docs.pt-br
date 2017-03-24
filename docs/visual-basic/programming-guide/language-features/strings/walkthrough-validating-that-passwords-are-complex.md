---
title: "Validação de complexidade de senhas (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- String data type, validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e899900d60bddb83fb640abcc7f11f333c1af870
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>Instruções passo a passo: validando senhas complexas (Visual Basic)
Esse método verifica se há algumas características de senhas robustas e atualiza um parâmetro de cadeia de caracteres com informações sobre em quais quesitos a senha falha.  
  
 Senhas podem ser usadas em um sistema seguro para autenticar um usuário. No entanto, as senhas devem ser difícil para usuários não autorizados de adivinhar. Os invasores podem usar um *ataque de dicionário* programa, que percorre todas as palavras em um dicionário (ou vários dicionários em linguagens diferentes) e teste se alguma das palavras funciona como uma senha de usuário. Senhas fracas, como "Yankees" ou "Mustang" podem ser adivinhadas facilmente. Senhas mais fortes, como "? Você 'L1N3vaFiNdMeyeP@sSWerd! ", são muito menos prováveis de serem adivinhadas. Um sistema protegido por senha deve assegurar que os usuários escolham senhas fortes.  
  
 Uma senha forte é complexa (contendo uma mistura de caracteres maiusculo, minúsculos, numérico e especial) e não é uma palavra. Este exemplo demonstra como verificar a complexidade.  
  
## <a name="example"></a>Exemplo  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbcnRegEx n º&1;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Chame este método passando a cadeia de caracteres que contém a senha.  
  
 Este exemplo requer:  
  
-   Acesso aos membros do <xref:System.Text.RegularExpressions>namespace.</xref:System.Text.RegularExpressions> Adicione um `Imports` instrução se você não está qualificando totalmente nomes de membros em seu código. Para obter mais informações, consulte [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Segurança  
 Se você estiver movendo a senha em uma rede, você precisa usar um método seguro para transferência de dados. Para obter mais informações, consulte [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).  
  
 Você pode aumentar a precisão do `ValidatePassword` função adicionando verificações de complexidade adicionais:  
  
-   Compare seus subcadeias de caracteres em um dicionário definido pelo aplicativo, o identificador de usuário e o nome do usuário e a senha. Além disso, trate caracteres visualmente similares como equivalentes quando fizer as comparações. Por exemplo, trate as letras "l" e "e" como equivalentes aos numerais "1" e "3".  
  
-   Se houver apenas um caractere maiusculo, certifique-se de não é o primeiro caractere do password.  
  
-   Certifique-se de que os dois últimos caracteres da senha são letras.  
  
-   Não permita senhas em que todos os símbolos são inseridos na linha superior do teclado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Text.RegularExpressions.Regex></xref:System.Text.RegularExpressions.Regex>   
 [Segurança de aplicativo Web ASP .NET](https://msdn.microsoft.com/library/330a99hc)
