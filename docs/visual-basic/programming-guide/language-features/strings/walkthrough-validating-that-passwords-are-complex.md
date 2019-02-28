---
title: Validação de complexidade de senhas (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: fb95871f347bf1093701a428a8b925f884d17a56
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979691"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="20a76-102">Passo a passo: Validando senhas complexas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20a76-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="20a76-103">Esse método verifica se há algumas características de senha forte e atualiza um parâmetro de cadeia de caracteres com informações sobre em quais verificações de senha falha.</span><span class="sxs-lookup"><span data-stu-id="20a76-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="20a76-104">Senhas podem ser usadas em um sistema seguro para autorizar um usuário.</span><span class="sxs-lookup"><span data-stu-id="20a76-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="20a76-105">No entanto, as senhas devem ser difícil para usuários não autorizados estimem.</span><span class="sxs-lookup"><span data-stu-id="20a76-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="20a76-106">Os invasores podem usar um *ataque de dicionário* programa, que itera por meio de todas as palavras em um dicionário (ou vários dicionários em linguagens diferentes) e teste se qualquer uma das palavras funciona como uma senha de usuário.</span><span class="sxs-lookup"><span data-stu-id="20a76-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="20a76-107">Senhas fracas, como "Yankees" ou "Mustang" podem ser adivinhadas facilmente.</span><span class="sxs-lookup"><span data-stu-id="20a76-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="20a76-108">Senhas mais fortes, como "? Você 'L1N3vaFiNdMeyeP@sSWerd! ", são muito menos provável de ser adivinhada.</span><span class="sxs-lookup"><span data-stu-id="20a76-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="20a76-109">Um sistema protegido por senha deve garantir que os usuários escolham senhas fortes.</span><span class="sxs-lookup"><span data-stu-id="20a76-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="20a76-110">Uma senha forte é complexa (que contém uma mistura de caracteres maiusculos, minúsculos, numérico e especial) e não é uma palavra.</span><span class="sxs-lookup"><span data-stu-id="20a76-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="20a76-111">Este exemplo demonstra como verificar a complexidade.</span><span class="sxs-lookup"><span data-stu-id="20a76-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20a76-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20a76-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="20a76-113">Código</span><span class="sxs-lookup"><span data-stu-id="20a76-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="20a76-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="20a76-114">Compiling the Code</span></span>  
 <span data-ttu-id="20a76-115">Chame esse método, passando a cadeia de caracteres que contém a senha.</span><span class="sxs-lookup"><span data-stu-id="20a76-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="20a76-116">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="20a76-116">This example requires:</span></span>  
  
-   <span data-ttu-id="20a76-117">Acesso aos membros do namespace <xref:System.Text.RegularExpressions>.</span><span class="sxs-lookup"><span data-stu-id="20a76-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="20a76-118">Adicione uma instrução `Imports` se você não está qualificando totalmente os nomes de membros em seu código.</span><span class="sxs-lookup"><span data-stu-id="20a76-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="20a76-119">Para obter mais informações, consulte [Instrução Imports (tipo e namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="20a76-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="20a76-120">Segurança</span><span class="sxs-lookup"><span data-stu-id="20a76-120">Security</span></span>  
 <span data-ttu-id="20a76-121">Se você estiver movendo a senha em uma rede, você precisa usar um método seguro para a transferência de dados.</span><span class="sxs-lookup"><span data-stu-id="20a76-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="20a76-122">Para obter mais informações, consulte [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="20a76-122">For more information, see [ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="20a76-123">Você pode melhorar a precisão do `ValidatePassword` função adicionando verificações de complexidade adicional:</span><span class="sxs-lookup"><span data-stu-id="20a76-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
-   <span data-ttu-id="20a76-124">Compare a senha e suas substrings com o nome do usuário, o identificador de usuário e um dicionário definido pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="20a76-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="20a76-125">Além disso, trate caracteres visualmente similares como equivalentes ao realizar as comparações.</span><span class="sxs-lookup"><span data-stu-id="20a76-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="20a76-126">Por exemplo, trate as letras "l" e "e" como equivalentes aos numerais "1" e "3".</span><span class="sxs-lookup"><span data-stu-id="20a76-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
-   <span data-ttu-id="20a76-127">Se houver apenas um caractere maiusculo, certifique-se de não é o primeiro caractere do password.</span><span class="sxs-lookup"><span data-stu-id="20a76-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
-   <span data-ttu-id="20a76-128">Certifique-se de que os dois últimos caracteres da senha são caracteres de letras.</span><span class="sxs-lookup"><span data-stu-id="20a76-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
-   <span data-ttu-id="20a76-129">Não permita senhas em que todos os símbolos são inseridos na linha de parte superior do teclado.</span><span class="sxs-lookup"><span data-stu-id="20a76-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a76-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20a76-130">See also</span></span>
- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="20a76-131">[Segurança de aplicativo Web ASP .NET](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="20a76-131">[ASP.NET Web Application Security](https://docs.microsoft.com/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
