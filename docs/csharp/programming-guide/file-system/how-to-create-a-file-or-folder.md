---
title: "Como criar um arquivo ou uma pasta (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 150190eeef829bd0431eeea7789025b9905553e3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="730d6-102">Como criar um arquivo ou uma pasta (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="730d6-102">How to: Create a File or Folder (C# Programming Guide)</span></span>
<span data-ttu-id="730d6-103">Você pode criar uma pasta no seu computador, criar uma subpasta, criar um arquivo na subpasta e gravar dados no arquivo programaticamente.</span><span class="sxs-lookup"><span data-stu-id="730d6-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="730d6-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="730d6-104">Example</span></span>  
 <span data-ttu-id="730d6-105">[!code-cs[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="730d6-105">[!code-cs[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]</span></span>  
  
 <span data-ttu-id="730d6-106">Se a pasta já existir, <xref:System.IO.Directory.CreateDirectory%2A> não fará nada, e nenhuma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="730d6-106">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="730d6-107">No entanto, <xref:System.IO.File.Create%2A?displayProperty=fullName> substituirá um arquivo existente por um novo.</span><span class="sxs-lookup"><span data-stu-id="730d6-107">However, <xref:System.IO.File.Create%2A?displayProperty=fullName> replaces an existing file with a new file.</span></span> <span data-ttu-id="730d6-108">O exemplo usa uma instrução `if`-`else` para impedir que um arquivo existente seja substituído.</span><span class="sxs-lookup"><span data-stu-id="730d6-108">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="730d6-109">Fazendo as alterações a seguir no exemplo, você pode especificar diferentes resultados com base em se já existe um arquivo com um determinado nome.</span><span class="sxs-lookup"><span data-stu-id="730d6-109">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="730d6-110">Se esse arquivo não existir, o código criará um.</span><span class="sxs-lookup"><span data-stu-id="730d6-110">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="730d6-111">Se esse arquivo existir, o código acrescentará dados a esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="730d6-111">If such a file exists, the code appends data to that file.</span></span>  
  
-   <span data-ttu-id="730d6-112">Especifique um nome de arquivo não aleatório.</span><span class="sxs-lookup"><span data-stu-id="730d6-112">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
-   <span data-ttu-id="730d6-113">Substitua a instrução `if`-`else` pela instrução `using` no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="730d6-113">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="730d6-114">Execute o exemplo várias vezes para verificar se os dados são adicionados ao arquivo a cada vez.</span><span class="sxs-lookup"><span data-stu-id="730d6-114">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="730d6-115">Para ver mais valores `FileMode` que você pode tentar, consulte <xref:System.IO.FileMode>.</span><span class="sxs-lookup"><span data-stu-id="730d6-115">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="730d6-116">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="730d6-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="730d6-117">O nome da pasta está malformado.</span><span class="sxs-lookup"><span data-stu-id="730d6-117">The folder name is malformed.</span></span> <span data-ttu-id="730d6-118">Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (classe <xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="730d6-118">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="730d6-119">Use a classe <xref:System.IO.Path> para criar nomes de caminho válidos.</span><span class="sxs-lookup"><span data-stu-id="730d6-119">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
-   <span data-ttu-id="730d6-120">A pasta pai da pasta a ser criada é somente leitura (classe <xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="730d6-120">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="730d6-121">O nome da pasta é `null` (classe <xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="730d6-121">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="730d6-122">O nome da pasta é longo demais (classe <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="730d6-122">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="730d6-123">O nome da pasta contém apenas dois-pontos, “:” (classe <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="730d6-123">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="730d6-124">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="730d6-124">.NET Framework Security</span></span>  
 <span data-ttu-id="730d6-125">Uma instância da classe <xref:System.Security.SecurityException> poderá ser gerada em situações de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="730d6-125">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="730d6-126">Se você não tiver permissão para criar a pasta, o exemplo gerará uma instância da classe <xref:System.UnauthorizedAccessException>.</span><span class="sxs-lookup"><span data-stu-id="730d6-126">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730d6-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="730d6-127">See Also</span></span>  
 <span data-ttu-id="730d6-128"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="730d6-128"><xref:System.IO?displayProperty=fullName></span></span>   
 <span data-ttu-id="730d6-129">[Guia de programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="730d6-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="730d6-130">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="730d6-130">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)

