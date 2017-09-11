---
title: Compilando aplicativos de console no .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bba3cde0d4e1c15ea764322b8ab0ef1501e53739
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="building-console-applications-in-the-net-framework"></a><span data-ttu-id="d86ac-102">Compilando aplicativos de console no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d86ac-102">Building Console Applications in the .NET Framework</span></span>
<span data-ttu-id="d86ac-103">Os aplicativos do .NET Framework podem usar a classe <xref:System.Console?displayProperty=fullName> para ler e gravar caracteres no console.</span><span class="sxs-lookup"><span data-stu-id="d86ac-103">Applications in the .NET Framework can use the <xref:System.Console?displayProperty=fullName> class to read characters from and write characters to the console.</span></span> <span data-ttu-id="d86ac-104">Os dados do console são lidos a partir do fluxo de entrada padrão, os dados para o console são gravados no fluxo de saída padrão e os dados de erro do console são gravados no fluxo de saída de erro padrão.</span><span class="sxs-lookup"><span data-stu-id="d86ac-104">Data from the console is read from the standard input stream, data to the console is written to the standard output stream, and error data to the console is written to the standard error output stream.</span></span> <span data-ttu-id="d86ac-105">Esses fluxos são automaticamente associados ao console quando o aplicativo é iniciado e são apresentados como as propriedades <xref:System.Console.In%2A>, <xref:System.Console.Out%2A> e <xref:System.Console.Error%2A>, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d86ac-105">These streams are automatically associated with the console when the application starts and are presented as the <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, and <xref:System.Console.Error%2A> properties, respectively.</span></span>  
  
 <span data-ttu-id="d86ac-106">O valor da propriedade <xref:System.Console.In%2A?displayProperty=fullName> é um objeto <xref:System.IO.TextReader?displayProperty=fullName>, ao passo que os valores das propriedades <xref:System.Console.Out%2A?displayProperty=fullName> e <xref:System.Console.Error%2A?displayProperty=fullName> são objetos <xref:System.IO.TextWriter?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d86ac-106">The value of the <xref:System.Console.In%2A?displayProperty=fullName> property is a <xref:System.IO.TextReader?displayProperty=fullName> object, whereas the values of the <xref:System.Console.Out%2A?displayProperty=fullName> and <xref:System.Console.Error%2A?displayProperty=fullName> properties are <xref:System.IO.TextWriter?displayProperty=fullName> objects.</span></span> <span data-ttu-id="d86ac-107">Você pode associar essas propriedades com fluxos que não representam o console, tornando possível apontar para o fluxo em um local diferente de entrada ou saída.</span><span class="sxs-lookup"><span data-stu-id="d86ac-107">You can associate these properties with streams that do not represent the console, making it possible for you to point the stream to a different location for input or output.</span></span> <span data-ttu-id="d86ac-108">Por exemplo, você pode redirecionar a saída para um arquivo ao definir a propriedade <xref:System.Console.Out%2A?displayProperty=fullName> para um <xref:System.IO.StreamWriter?displayProperty=fullName> que encapsula um <xref:System.IO.FileStream?displayProperty=fullName> pelo método <xref:System.Console.SetOut%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d86ac-108">For example, you can redirect the output to a file by setting the <xref:System.Console.Out%2A?displayProperty=fullName> property to a <xref:System.IO.StreamWriter?displayProperty=fullName>, which encapsulates a <xref:System.IO.FileStream?displayProperty=fullName> by means of the <xref:System.Console.SetOut%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="d86ac-109">As propriedades <xref:System.Console.In%2A?displayProperty=fullName> e <xref:System.Console.Out%2A?displayProperty=fullName> não precisam fazer referência ao mesmo fluxo.</span><span class="sxs-lookup"><span data-stu-id="d86ac-109">The <xref:System.Console.In%2A?displayProperty=fullName> and <xref:System.Console.Out%2A?displayProperty=fullName> properties do not need to refer to the same stream.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d86ac-110">Para mais informações sobre a compilação de aplicativos de console, incluindo exemplos em C #, Visual Basic e C++, consulte a documentação da classe <xref:System.Console>.</span><span class="sxs-lookup"><span data-stu-id="d86ac-110">For more information about building console applications, including examples in C#, Visual Basic, and C++, see the documentation for the <xref:System.Console> class.</span></span>  
  
 <span data-ttu-id="d86ac-111">Se o console não existir, como em um aplicativo baseado no Windows, a gravação de saída no fluxo de saída padrão não será visível, uma vez que não haverá nenhum console para gravar as informações.</span><span class="sxs-lookup"><span data-stu-id="d86ac-111">If the console does not exist, as in a Windows-based application, output written to the standard output stream will not be visible, because there is no console to write the information to.</span></span> <span data-ttu-id="d86ac-112">A gravação de informações em um console inacessível não gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d86ac-112">Writing information to an inaccessible console does not cause an exception to be raised.</span></span>  
  
 <span data-ttu-id="d86ac-113">Como alternativa, para permitir que o console leia e grave em um aplicativo baseado no Windows que foi desenvolvido usando o Visual Studio, abra a caixa de diálogo **Propriedades** do projeto, clique na guia **Aplicativo** e defina **Tipo de aplicativo** como **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="d86ac-113">Alternately, to enable the console for reading and writing within a Windows-based application that is developed using Visual Studio, open the project's **Properties** dialog box, click the **Application** tab, and set the **Application type** to **Console Application**.</span></span>  
  
 <span data-ttu-id="d86ac-114">Nos aplicativos de console falta uma bomba de mensagem iniciada por padrão.</span><span class="sxs-lookup"><span data-stu-id="d86ac-114">Console applications lack a message pump that starts by default.</span></span> <span data-ttu-id="d86ac-115">Portanto, as chamadas do console para os temporizadores do Microsoft Win32 podem falhar.</span><span class="sxs-lookup"><span data-stu-id="d86ac-115">Therefore, console calls to Microsoft Win32 timers might fail.</span></span>  
  
 <span data-ttu-id="d86ac-116">A classe **System.Console** tem métodos que podem ler caracteres individuais ou linhas inteiras do console.</span><span class="sxs-lookup"><span data-stu-id="d86ac-116">The **System.Console** class has methods that can read individual characters or entire lines from the console.</span></span> <span data-ttu-id="d86ac-117">Outros métodos convertem dados e cadeias de formato e gravam as cadeias formatadas no console.</span><span class="sxs-lookup"><span data-stu-id="d86ac-117">Other methods convert data and format strings, and then write the formatted strings to the console.</span></span> <span data-ttu-id="d86ac-118">Para mais informações sobre cadeias de caracteres de formatação, consulte [Tipos de formatação](../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="d86ac-118">For more information on formatting strings, see [Formatting Types](../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d86ac-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d86ac-119">See Also</span></span>  
 <span data-ttu-id="d86ac-120"><xref:System.Console?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d86ac-120"><xref:System.Console?displayProperty=fullName></span></span>   
 [<span data-ttu-id="d86ac-121">Formatando Tipos</span><span class="sxs-lookup"><span data-stu-id="d86ac-121">Formatting Types</span></span>](../../docs/standard/base-types/formatting-types.md)

