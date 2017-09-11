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
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8d636c1e43de6a108cdc217cb21aaf7689e175f7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="73ada-102">Instruções passo a passo: validando senhas complexas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73ada-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="73ada-103">Esse método verifica se há algumas características de senhas robustas e atualiza um parâmetro de cadeia de caracteres com informações sobre em quais quesitos a senha falha.</span><span class="sxs-lookup"><span data-stu-id="73ada-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="73ada-104">Senhas podem ser usadas em um sistema seguro para autenticar um usuário.</span><span class="sxs-lookup"><span data-stu-id="73ada-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="73ada-105">No entanto, as senhas devem ser difícil para usuários não autorizados de adivinhar.</span><span class="sxs-lookup"><span data-stu-id="73ada-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="73ada-106">Os invasores podem usar um *ataque de dicionário* programa, que percorre todas as palavras em um dicionário (ou vários dicionários em linguagens diferentes) e teste se alguma das palavras funciona como uma senha de usuário.</span><span class="sxs-lookup"><span data-stu-id="73ada-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="73ada-107">Senhas fracas, como "Yankees" ou "Mustang" podem ser adivinhadas facilmente.</span><span class="sxs-lookup"><span data-stu-id="73ada-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="73ada-108">Senhas mais fortes, como "? Você 'L1N3vaFiNdMeyeP@sSWerd! ", são muito menos prováveis de serem adivinhadas.</span><span class="sxs-lookup"><span data-stu-id="73ada-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="73ada-109">Um sistema protegido por senha deve assegurar que os usuários escolham senhas fortes.</span><span class="sxs-lookup"><span data-stu-id="73ada-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="73ada-110">Uma senha forte é complexa (contendo uma mistura de caracteres maiusculo, minúsculos, numérico e especial) e não é uma palavra.</span><span class="sxs-lookup"><span data-stu-id="73ada-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="73ada-111">Este exemplo demonstra como verificar a complexidade.</span><span class="sxs-lookup"><span data-stu-id="73ada-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73ada-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="73ada-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="73ada-113">Código</span><span class="sxs-lookup"><span data-stu-id="73ada-113">Code</span></span>  
 <span data-ttu-id="73ada-114">[!code-vb[VbVbcnRegEx n º&1;](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="73ada-114">[!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="73ada-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="73ada-115">Compiling the Code</span></span>  
 <span data-ttu-id="73ada-116">Chame este método passando a cadeia de caracteres que contém a senha.</span><span class="sxs-lookup"><span data-stu-id="73ada-116">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="73ada-117">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="73ada-117">This example requires:</span></span>  
  
-   <span data-ttu-id="73ada-118">Acesso aos membros do <xref:System.Text.RegularExpressions>namespace.</xref:System.Text.RegularExpressions></span><span class="sxs-lookup"><span data-stu-id="73ada-118">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="73ada-119">Adicione um `Imports` instrução se você não está qualificando totalmente nomes de membros em seu código.</span><span class="sxs-lookup"><span data-stu-id="73ada-119">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="73ada-120">Para obter mais informações, consulte [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="73ada-120">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="73ada-121">Segurança</span><span class="sxs-lookup"><span data-stu-id="73ada-121">Security</span></span>  
 <span data-ttu-id="73ada-122">Se você estiver movendo a senha em uma rede, você precisa usar um método seguro para transferência de dados.</span><span class="sxs-lookup"><span data-stu-id="73ada-122">If you are moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="73ada-123">Para obter mais informações, consulte [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span><span class="sxs-lookup"><span data-stu-id="73ada-123">For more information, see [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span></span>  
  
 <span data-ttu-id="73ada-124">Você pode aumentar a precisão do `ValidatePassword` função adicionando verificações de complexidade adicionais:</span><span class="sxs-lookup"><span data-stu-id="73ada-124">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="73ada-125">Compare seus subcadeias de caracteres em um dicionário definido pelo aplicativo, o identificador de usuário e o nome do usuário e a senha.</span><span class="sxs-lookup"><span data-stu-id="73ada-125">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="73ada-126">Além disso, trate caracteres visualmente similares como equivalentes quando fizer as comparações.</span><span class="sxs-lookup"><span data-stu-id="73ada-126">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="73ada-127">Por exemplo, trate as letras "l" e "e" como equivalentes aos numerais "1" e "3".</span><span class="sxs-lookup"><span data-stu-id="73ada-127">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="73ada-128">Se houver apenas um caractere maiusculo, certifique-se de não é o primeiro caractere do password.</span><span class="sxs-lookup"><span data-stu-id="73ada-128">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="73ada-129">Certifique-se de que os dois últimos caracteres da senha são letras.</span><span class="sxs-lookup"><span data-stu-id="73ada-129">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="73ada-130">Não permita senhas em que todos os símbolos são inseridos na linha superior do teclado.</span><span class="sxs-lookup"><span data-stu-id="73ada-130">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ada-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73ada-131">See Also</span></span>  
 <span data-ttu-id="73ada-132"><xref:System.Text.RegularExpressions.Regex></xref:System.Text.RegularExpressions.Regex></span><span class="sxs-lookup"><span data-stu-id="73ada-132"><xref:System.Text.RegularExpressions.Regex></span></span>   
<span data-ttu-id="73ada-133"> [Segurança de aplicativo Web ASP .NET](https://msdn.microsoft.com/library/330a99hc)</span><span class="sxs-lookup"><span data-stu-id="73ada-133"> [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc)</span></span>
