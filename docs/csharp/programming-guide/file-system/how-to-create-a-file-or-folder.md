---
title: Como criar um arquivo ou pasta-guia de programação C#
description: Saiba como criar um arquivo ou uma pasta programaticamente. Você pode criar uma pasta, uma subpasta, um arquivo na subpasta e gravar dados nesse arquivo.
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: f5641dc765b1a2d62adb76babe3f111730d4550b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302679"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="04f62-104">Como criar um arquivo ou uma pasta (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="04f62-104">How to create a file or folder (C# Programming Guide)</span></span>
<span data-ttu-id="04f62-105">Você pode criar uma pasta no seu computador, criar uma subpasta, criar um arquivo na subpasta e gravar dados no arquivo programaticamente.</span><span class="sxs-lookup"><span data-stu-id="04f62-105">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04f62-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04f62-106">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="04f62-107">Se a pasta já existir, <xref:System.IO.Directory.CreateDirectory%2A> não fará nada, e nenhuma exceção será gerada.</span><span class="sxs-lookup"><span data-stu-id="04f62-107">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="04f62-108">No entanto, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> substituirá um arquivo existente por um novo.</span><span class="sxs-lookup"><span data-stu-id="04f62-108">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="04f62-109">O exemplo usa uma instrução `if`-`else` para impedir que um arquivo existente seja substituído.</span><span class="sxs-lookup"><span data-stu-id="04f62-109">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="04f62-110">Fazendo as alterações a seguir no exemplo, você pode especificar diferentes resultados com base em se já existe um arquivo com um determinado nome.</span><span class="sxs-lookup"><span data-stu-id="04f62-110">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="04f62-111">Se esse arquivo não existir, o código criará um.</span><span class="sxs-lookup"><span data-stu-id="04f62-111">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="04f62-112">Se esse arquivo existir, o código acrescentará dados a esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="04f62-112">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="04f62-113">Especifique um nome de arquivo não aleatório.</span><span class="sxs-lookup"><span data-stu-id="04f62-113">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="04f62-114">Substitua a instrução `if`-`else` pela instrução `using` no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="04f62-114">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="04f62-115">Execute o exemplo várias vezes para verificar se os dados são adicionados ao arquivo a cada vez.</span><span class="sxs-lookup"><span data-stu-id="04f62-115">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="04f62-116">Para ver mais valores `FileMode` que você pode tentar, consulte <xref:System.IO.FileMode>.</span><span class="sxs-lookup"><span data-stu-id="04f62-116">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="04f62-117">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="04f62-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="04f62-118">O nome da pasta está malformado.</span><span class="sxs-lookup"><span data-stu-id="04f62-118">The folder name is malformed.</span></span> <span data-ttu-id="04f62-119">Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (classe <xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="04f62-119">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="04f62-120">Use a classe <xref:System.IO.Path> para criar nomes de caminho válidos.</span><span class="sxs-lookup"><span data-stu-id="04f62-120">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="04f62-121">A pasta pai da pasta a ser criada é somente leitura (classe <xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="04f62-121">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="04f62-122">O nome da pasta é `null` (classe <xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="04f62-122">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="04f62-123">O nome da pasta é longo demais (classe <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="04f62-123">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="04f62-124">O nome da pasta contém apenas dois-pontos, “:” (classe <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="04f62-124">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="04f62-125">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="04f62-125">.NET Security</span></span>  
 <span data-ttu-id="04f62-126">Uma instância da classe <xref:System.Security.SecurityException> poderá ser gerada em situações de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="04f62-126">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="04f62-127">Se você não tiver permissão para criar a pasta, o exemplo lançará uma instância da <xref:System.UnauthorizedAccessException> classe.</span><span class="sxs-lookup"><span data-stu-id="04f62-127">If you don't have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f62-128">Veja também</span><span class="sxs-lookup"><span data-stu-id="04f62-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="04f62-129">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="04f62-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="04f62-130">Sistema de arquivos e o Registro (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="04f62-130">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
