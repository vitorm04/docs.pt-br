---
title: Como excluir uma chave do Registro no Visual Basic
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.DeleteSetting
dev_langs:
- VB
helpviewer_keywords:
- GetSetting function
- registry, deleting values
- GetAllSettings function
- registry keys, deleting
- registry, deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
caps.latest.revision: 28
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0fc37aff9f6a0ae3a7953377ebf95179d01bb693
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="e99fb-102">Como excluir uma chave do Registro no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e99fb-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="e99fb-103">Os métodos <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> e <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> podem ser usados para excluir chaves do Registro.</span><span class="sxs-lookup"><span data-stu-id="e99fb-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="e99fb-104">Procedimento</span><span class="sxs-lookup"><span data-stu-id="e99fb-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="e99fb-105">Excluir uma chave do Registro</span><span class="sxs-lookup"><span data-stu-id="e99fb-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="e99fb-106">Use o método `DeleteSubKey` para excluir uma chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="e99fb-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="e99fb-107">Este exemplo exclui a chave Software/TestApp no hive CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="e99fb-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="e99fb-108">É possível alterar isso no código para a cadeia de caracteres apropriada ou fazer com que se baseie nas informações fornecidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e99fb-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     <span data-ttu-id="e99fb-109">[!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e99fb-109">[!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e99fb-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="e99fb-110">Robust Programming</span></span>  
 <span data-ttu-id="e99fb-111">O método `DeleteSubKey` retornará uma cadeia de caracteres vazia se o par chave-valor não existir.</span><span class="sxs-lookup"><span data-stu-id="e99fb-111">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="e99fb-112">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="e99fb-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e99fb-113">O nome da chave é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="e99fb-113">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="e99fb-114">O usuário não tem permissões para excluir chaves do Registro (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="e99fb-114">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="e99fb-115">O nome da chave excede o limite de 255 caracteres (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e99fb-115">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="e99fb-116">A chave do Registro é somente leitura (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="e99fb-116">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e99fb-117">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e99fb-117">.NET Framework Security</span></span>  
 <span data-ttu-id="e99fb-118">As chamadas do Registro falharão se as permissões suficientes de tempo de execução não forem concedidas (<xref:System.Security.Permissions.RegistryPermission>) ou se o usuário não tiver o acesso correto para (conforme determinado pelas ACLs) para criar ou gravar nas configurações.</span><span class="sxs-lookup"><span data-stu-id="e99fb-118">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="e99fb-119">Por exemplo, um aplicativo local que tem a permissão de segurança de acesso do código pode não ter permissão do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="e99fb-119">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e99fb-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e99fb-120">See Also</span></span>  
 <span data-ttu-id="e99fb-121"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="e99fb-121"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span></span>   
 <span data-ttu-id="e99fb-122"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="e99fb-122"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span></span>   
 <span data-ttu-id="e99fb-123"><xref:Microsoft.Win32.RegistryKey></span><span class="sxs-lookup"><span data-stu-id="e99fb-123"><xref:Microsoft.Win32.RegistryKey></span></span>   
 <span data-ttu-id="e99fb-124">[Segurança e Registro](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="e99fb-124">[Security and the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md) </span></span>  
 [<span data-ttu-id="e99fb-125">Lendo e Gravando do Registro</span><span class="sxs-lookup"><span data-stu-id="e99fb-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)

