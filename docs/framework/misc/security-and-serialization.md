---
title: "Segurança e serialização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a870834b86f1ed99181614278a7381932a18ac8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-and-serialization"></a><span data-ttu-id="b5ee0-102">Segurança e serialização</span><span class="sxs-lookup"><span data-stu-id="b5ee0-102">Security and Serialization</span></span>
<span data-ttu-id="b5ee0-103">Como a serialização pode permitir que outro código ver ou modificar dados de instância de objeto que possa ser acessados, uma permissão especial é necessária de código para executar a serialização: <xref:System.Security.Permissions.SecurityPermission> com o <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> sinalizador especificado.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="b5ee0-104">De acordo com a política padrão, essa permissão não é dada ao código da intranet ou baixado da Internet; somente o código no computador local recebe essa permissão.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="b5ee0-105">Normalmente, todos os campos de uma instância do objeto são serializados, que significa que os dados são representados nos dados serializados para a instância.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="b5ee0-106">É possível para o código que pode interpretar o formato para determinar quais os valores de dados, independentemente de acessibilidade do membro.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="b5ee0-107">Da mesma forma, desserialização extrai dados da representação serializada e define o estado do objeto diretamente, novamente independentemente de regras de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="b5ee0-108">Qualquer objeto que pode conter dados confidenciais deve ser feito nonserializable, se possível.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="b5ee0-109">Se ele deve ser serializável, tente fazer campos específicos que contêm dados confidenciais serializável.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="b5ee0-110">Se isso não pode ser feito, lembre-se de que esses dados serão expostos a qualquer código que tem permissão para serializar e certifique-se de que nenhum código mal-intencionado pode obter essa permissão.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="b5ee0-111">O <xref:System.Runtime.Serialization.ISerializable> interface é destinada ao uso somente pela infraestrutura de serialização.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="b5ee0-112">No entanto, se desprotegidos, ele pode liberar potencialmente informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="b5ee0-113">Se você fornecer a serialização personalizada implementando **ISerializable**, certifique-se de tomar as seguintes precauções:</span><span class="sxs-lookup"><span data-stu-id="b5ee0-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
-   <span data-ttu-id="b5ee0-114">O <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método deve ser explicitamente protegido por mais exigentes o **SecurityPermission** com **comoSerializationFormatter** permissão especificado ou por certificando-se de que não diferencia informações são liberadas com a saída do método.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="b5ee0-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b5ee0-115">For example:</span></span>  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Sub GetObjectData(info As SerializationInfo, context As StreamingContext)  
    End Sub  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter   
    =true)]  
    public override void GetObjectData(SerializationInfo info,   
    StreamingContext context)  
    {  
    }  
    ```  
  
-   <span data-ttu-id="b5ee0-116">O construtor especial usado para serialização também deve executar a validação da entrada completa e deve ser protegida ou privada para ajudar a proteger contra o uso indevido por códigos mal-intencionados.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="b5ee0-117">Ele deve aplicar o mesmo verificações de segurança e permissões necessárias para obter uma instância dessa classe por outros meios, como criar explicitamente a classe ou indiretamente criá-lo por meio de algum tipo de fábrica.</span><span class="sxs-lookup"><span data-stu-id="b5ee0-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ee0-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5ee0-118">See Also</span></span>  
 [<span data-ttu-id="b5ee0-119">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="b5ee0-119">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
