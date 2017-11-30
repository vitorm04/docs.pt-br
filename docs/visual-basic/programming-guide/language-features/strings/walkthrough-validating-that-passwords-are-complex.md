---
title: "Validação de complexidade de senhas (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdbe5f385c6b7a0898c4907b0d8afabdaed06fa0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="12319-102">Instruções passo a passo: validando senhas complexas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12319-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="12319-103">Este método verifica se há algumas características de senha forte e atualiza um parâmetro de cadeia de caracteres com informações sobre quais verifica a senha falha.</span><span class="sxs-lookup"><span data-stu-id="12319-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="12319-104">Senhas podem ser usadas em um sistema seguro para autorizar um usuário.</span><span class="sxs-lookup"><span data-stu-id="12319-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="12319-105">No entanto, as senhas devem ser difícil para usuários não autorizados estimem.</span><span class="sxs-lookup"><span data-stu-id="12319-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="12319-106">Os invasores podem usar um *ataque de dicionário* programa que itera por meio de todas as palavras de um dicionário (ou vários dicionários em idiomas diferentes) e teste se alguma das palavras funciona como uma senha de usuário.</span><span class="sxs-lookup"><span data-stu-id="12319-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="12319-107">Senhas fracas como "Yankees" ou "Mustang" podem ser adivinhadas rapidamente.</span><span class="sxs-lookup"><span data-stu-id="12319-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="12319-108">Senhas de alto nível, como "? Você 'L1N3vaFiNdMeyeP@sSWerd! ", são muito menos prováveis de ser adivinhada.</span><span class="sxs-lookup"><span data-stu-id="12319-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="12319-109">Um sistema protegido por senha deve garantir que os usuários escolham senhas fortes.</span><span class="sxs-lookup"><span data-stu-id="12319-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="12319-110">Uma senha forte é complexa (que contém uma mistura de caracteres maiusculo, minúsculo, numérico e especial) e não é uma palavra.</span><span class="sxs-lookup"><span data-stu-id="12319-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="12319-111">Este exemplo demonstra como verificar a complexidade.</span><span class="sxs-lookup"><span data-stu-id="12319-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12319-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12319-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="12319-113">Código</span><span class="sxs-lookup"><span data-stu-id="12319-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/walkthrough-validating-that-passwords-are-complex_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="12319-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="12319-114">Compiling the Code</span></span>  
 <span data-ttu-id="12319-115">Chame este método passando a cadeia de caracteres que contém a senha.</span><span class="sxs-lookup"><span data-stu-id="12319-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="12319-116">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="12319-116">This example requires:</span></span>  
  
-   <span data-ttu-id="12319-117">Acesso aos membros do namespace <xref:System.Text.RegularExpressions>.</span><span class="sxs-lookup"><span data-stu-id="12319-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="12319-118">Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código.</span><span class="sxs-lookup"><span data-stu-id="12319-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="12319-119">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="12319-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="12319-120">Segurança</span><span class="sxs-lookup"><span data-stu-id="12319-120">Security</span></span>  
 <span data-ttu-id="12319-121">Se você estiver movendo a senha em uma rede, você precisa usar um método seguro de transferência de dados.</span><span class="sxs-lookup"><span data-stu-id="12319-121">If you are moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="12319-122">Para obter mais informações, consulte [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span><span class="sxs-lookup"><span data-stu-id="12319-122">For more information, see [ASP.NET Web Application Security](https://msdn.microsoft.com/library/330a99hc).</span></span>  
  
 <span data-ttu-id="12319-123">Você pode melhorar a precisão do `ValidatePassword` função adicionando verificações de complexidade adicional:</span><span class="sxs-lookup"><span data-stu-id="12319-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="12319-124">Compare a senha e suas substrings com o nome do usuário, o identificador de usuário e um dicionário definido pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="12319-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="12319-125">Além disso, trate caracteres visualmente similares como equivalentes ao executar as comparações.</span><span class="sxs-lookup"><span data-stu-id="12319-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="12319-126">Por exemplo, trate as letras "l" e "e" como equivalentes aos numerais "1" e "3".</span><span class="sxs-lookup"><span data-stu-id="12319-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="12319-127">Se houver apenas um caractere maiusculo, certifique-se de não é o primeiro caractere do password.</span><span class="sxs-lookup"><span data-stu-id="12319-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="12319-128">Certifique-se de que os dois últimos caracteres da senha são letras.</span><span class="sxs-lookup"><span data-stu-id="12319-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="12319-129">Não permita senhas em que todos os símbolos são inseridos na linha superior do teclado.</span><span class="sxs-lookup"><span data-stu-id="12319-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12319-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12319-130">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex>  
 [<span data-ttu-id="12319-131">Segurança de aplicativo Web ASP .NET</span><span class="sxs-lookup"><span data-stu-id="12319-131">ASP.NET Web Application Security</span></span>](https://msdn.microsoft.com/library/330a99hc)
