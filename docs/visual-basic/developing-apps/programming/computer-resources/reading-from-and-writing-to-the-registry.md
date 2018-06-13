---
title: Lendo e gravando a partir do Registro (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: 6ce05b956ebf9a544eb8c95165b0f709c694f334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584612"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="3344b-102">Lendo e gravando a partir do Registro (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3344b-102">Reading from and Writing to the Registry (Visual Basic)</span></span>
<span data-ttu-id="3344b-103">Este tópico descreve as tarefas e tópicos conceituais associados ao Registro.</span><span class="sxs-lookup"><span data-stu-id="3344b-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="3344b-104">Ao programar em Visual Basic, você pode optar por acessar o Registro por meio das funções fornecidas pelo Visual Basic ou das classes de Registro do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3344b-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="3344b-105">O Registro hospeda informações do sistema operacional, bem como informações de aplicativos hospedados no computador.</span><span class="sxs-lookup"><span data-stu-id="3344b-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="3344b-106">Trabalhar com o Registro pode comprometer a segurança ao permitir o acesso inadequado aos recursos do sistema ou a informações protegidas.</span><span class="sxs-lookup"><span data-stu-id="3344b-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3344b-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3344b-107">In This Section</span></span>  
 [<span data-ttu-id="3344b-108">Como Criar uma Chave do Registro e Definir o Valor</span><span class="sxs-lookup"><span data-stu-id="3344b-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="3344b-109">Descreve como usar os métodos `CreateSubKey` e `SetValue` do objeto `My.Computer.Registry` para criar uma chave do Registro e definir seu valor.</span><span class="sxs-lookup"><span data-stu-id="3344b-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="3344b-110">Como Ler um Valor de uma Chave do Registro</span><span class="sxs-lookup"><span data-stu-id="3344b-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="3344b-111">Descreve como usar o método `GetValue` do objeto `My.Computer.Registry` para ler um valor de uma chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="3344b-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="3344b-112">Como Excluir uma Chave do Registro</span><span class="sxs-lookup"><span data-stu-id="3344b-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="3344b-113">Descreve como usar o método `DeleteSubKey` da propriedade `My.Computer.Registry.CurrentUser` para excluir uma chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="3344b-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="3344b-114">Lendo e Gravando no Registro Usando o Namespace Microsoft.Win32</span><span class="sxs-lookup"><span data-stu-id="3344b-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="3344b-115">Descreve como usar as classes `Registry` e `RegistryKey` do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] para acessar o Registro.</span><span class="sxs-lookup"><span data-stu-id="3344b-115">Describes how to use the `Registry` and `RegistryKey` classes of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to access the registry.</span></span>  
  
 [<span data-ttu-id="3344b-116">Segurança e Registro</span><span class="sxs-lookup"><span data-stu-id="3344b-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="3344b-117">Aborda questões de segurança que envolvem o Registro.</span><span class="sxs-lookup"><span data-stu-id="3344b-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3344b-118">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="3344b-118">Related Sections</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="3344b-119">Lista e explica membros do objeto `My.Computer.Registry`.</span><span class="sxs-lookup"><span data-stu-id="3344b-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="3344b-120">Apresenta uma visão geral da classe `Registry`, bem como links para membros e chaves individuais.</span><span class="sxs-lookup"><span data-stu-id="3344b-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
