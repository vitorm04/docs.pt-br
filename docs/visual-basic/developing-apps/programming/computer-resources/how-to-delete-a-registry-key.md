---
title: Como excluir uma chave do Registro no Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
ms.openlocfilehash: 8a983436b8c7415f0d356d65ae7d6c5ffd1c2db5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583845"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="c29a2-102">Como excluir uma chave do Registro no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c29a2-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="c29a2-103">Os métodos <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> e <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> podem ser usados para excluir chaves do Registro.</span><span class="sxs-lookup"><span data-stu-id="c29a2-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="c29a2-104">Procedimento</span><span class="sxs-lookup"><span data-stu-id="c29a2-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="c29a2-105">Excluir uma chave do Registro</span><span class="sxs-lookup"><span data-stu-id="c29a2-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="c29a2-106">Use o método `DeleteSubKey` para excluir uma chave do Registro.</span><span class="sxs-lookup"><span data-stu-id="c29a2-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="c29a2-107">Este exemplo exclui a chave Software/TestApp no hive CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="c29a2-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="c29a2-108">É possível alterar isso no código para a cadeia de caracteres apropriada ou fazer com que se baseie nas informações fornecidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="c29a2-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c29a2-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="c29a2-109">Robust Programming</span></span>  
 <span data-ttu-id="c29a2-110">O método `DeleteSubKey` retornará uma cadeia de caracteres vazia se o par chave-valor não existir.</span><span class="sxs-lookup"><span data-stu-id="c29a2-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="c29a2-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="c29a2-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c29a2-112">O nome da chave é `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="c29a2-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="c29a2-113">O usuário não tem permissões para excluir chaves do Registro (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="c29a2-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="c29a2-114">O nome da chave excede o limite de 255 caracteres (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="c29a2-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="c29a2-115">A chave do Registro é somente leitura (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="c29a2-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c29a2-116">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c29a2-116">.NET Framework Security</span></span>  
 <span data-ttu-id="c29a2-117">As chamadas do Registro falharão se as permissões suficientes de tempo de execução não forem concedidas (<xref:System.Security.Permissions.RegistryPermission>) ou se o usuário não tiver o acesso correto para (conforme determinado pelas ACLs) para criar ou gravar nas configurações.</span><span class="sxs-lookup"><span data-stu-id="c29a2-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="c29a2-118">Por exemplo, um aplicativo local que tem a permissão de segurança de acesso do código pode não ter permissão do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="c29a2-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c29a2-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c29a2-119">See Also</span></span>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey>  
 [<span data-ttu-id="c29a2-120">Segurança e Registro</span><span class="sxs-lookup"><span data-stu-id="c29a2-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 [<span data-ttu-id="c29a2-121">Lendo e Gravando do Registro</span><span class="sxs-lookup"><span data-stu-id="c29a2-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
