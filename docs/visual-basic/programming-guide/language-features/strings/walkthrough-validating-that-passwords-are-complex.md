---
title: Validando a complexidade de senhas
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 6e8697379a6fbb5cc15b60291e5b822897c2c013
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348324"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="6fab7-102">Instruções passo a passo: validando senhas complexas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fab7-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="6fab7-103">Esse método verifica algumas características de senha forte e atualiza um parâmetro de cadeia de caracteres com informações sobre quais verificações a senha falha.</span><span class="sxs-lookup"><span data-stu-id="6fab7-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="6fab7-104">As senhas podem ser usadas em um sistema seguro para autorizar um usuário.</span><span class="sxs-lookup"><span data-stu-id="6fab7-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="6fab7-105">No entanto, as senhas devem ser difíceis para que usuários não autorizados adivinhem.</span><span class="sxs-lookup"><span data-stu-id="6fab7-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="6fab7-106">Os invasores podem usar um programa de *ataque de dicionário* , que itera por todas as palavras em um dicionário (ou vários dicionários em diferentes idiomas) e testa se alguma das palavras funciona como uma senha de usuário.</span><span class="sxs-lookup"><span data-stu-id="6fab7-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="6fab7-107">Senhas fracas, como "Yankees" ou "Mustang", podem ser adivinhadas rapidamente.</span><span class="sxs-lookup"><span data-stu-id="6fab7-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="6fab7-108">Senhas mais fortes, como "? Você 'L1N3vaFiNdMeyeP@sSWerd! ", tem muito menos probabilidade de ser adivinhado.</span><span class="sxs-lookup"><span data-stu-id="6fab7-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="6fab7-109">Um sistema protegido por senha deve garantir que os usuários escolham senhas fortes.</span><span class="sxs-lookup"><span data-stu-id="6fab7-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="6fab7-110">Uma senha forte é complexa (contendo uma mistura de letras maiúsculas, letras minúsculas, números e caracteres especiais) e não é uma palavra.</span><span class="sxs-lookup"><span data-stu-id="6fab7-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="6fab7-111">Este exemplo demonstra como verificar a complexidade.</span><span class="sxs-lookup"><span data-stu-id="6fab7-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fab7-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6fab7-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="6fab7-113">Código</span><span class="sxs-lookup"><span data-stu-id="6fab7-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6fab7-114">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="6fab7-114">Compiling the Code</span></span>  
 <span data-ttu-id="6fab7-115">Chame esse método passando a cadeia de caracteres que contém essa senha.</span><span class="sxs-lookup"><span data-stu-id="6fab7-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="6fab7-116">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="6fab7-116">This example requires:</span></span>  
  
- <span data-ttu-id="6fab7-117">Acesso aos membros do namespace <xref:System.Text.RegularExpressions>.</span><span class="sxs-lookup"><span data-stu-id="6fab7-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="6fab7-118">Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código.</span><span class="sxs-lookup"><span data-stu-id="6fab7-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="6fab7-119">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="6fab7-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="6fab7-120">Segurança</span><span class="sxs-lookup"><span data-stu-id="6fab7-120">Security</span></span>  
 <span data-ttu-id="6fab7-121">Se estiver movendo a senha em uma rede, você precisará usar um método seguro para transferir dados.</span><span class="sxs-lookup"><span data-stu-id="6fab7-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="6fab7-122">Para obter mais informações, consulte [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6fab7-122">For more information, see [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="6fab7-123">Você pode melhorar a precisão da função `ValidatePassword` adicionando mais verificações de complexidade:</span><span class="sxs-lookup"><span data-stu-id="6fab7-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
- <span data-ttu-id="6fab7-124">Compare a senha e suas subcadeias de caracteres com o nome do usuário, o identificador de usuário e um dicionário definido pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6fab7-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="6fab7-125">Além disso, trate caracteres visualmente semelhantes como equivalentes ao executar as comparações.</span><span class="sxs-lookup"><span data-stu-id="6fab7-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="6fab7-126">Por exemplo, trate as letras "l" e "e" como equivalente aos numerais "1" e "3".</span><span class="sxs-lookup"><span data-stu-id="6fab7-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
- <span data-ttu-id="6fab7-127">Se houver apenas um caractere maiúsculo, verifique se ele não é o primeiro caractere da senha.</span><span class="sxs-lookup"><span data-stu-id="6fab7-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
- <span data-ttu-id="6fab7-128">Verifique se os dois últimos caracteres da senha são caracteres de letra.</span><span class="sxs-lookup"><span data-stu-id="6fab7-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
- <span data-ttu-id="6fab7-129">Não permita senhas em que todos os símbolos sejam inseridos da linha superior do teclado.</span><span class="sxs-lookup"><span data-stu-id="6fab7-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fab7-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fab7-130">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="6fab7-131">[Segurança de aplicativo Web ASP .NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6fab7-131">[ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
