---
title: Segurança e serialização
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, serialization
- serialization, security
- secure coding, serialization
- security [.NET Framework], serialization
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c275e7179daf0dfdf2dda8bf364a4682565f28a6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596728"
---
# <a name="security-and-serialization"></a><span data-ttu-id="f0c3a-102">Segurança e serialização</span><span class="sxs-lookup"><span data-stu-id="f0c3a-102">Security and Serialization</span></span>
<span data-ttu-id="f0c3a-103">Como a serialização pode permitir que outro código veja ou modifique os dados da instância de objeto de outro modo seria inacessíveis, uma permissão especial é necessária de código para executar a serialização: <xref:System.Security.Permissions.SecurityPermission> com o <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> sinalizador especificado.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-103">Because serialization can allow other code to see or modify object instance data that would otherwise be inaccessible, a special permission is required of code performing serialization: <xref:System.Security.Permissions.SecurityPermission> with the <xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="f0c3a-104">De acordo com a política padrão, essa permissão não é dada ao código da intranet ou baixado da Internet; somente o código no computador local recebe essa permissão.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-104">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span>  
  
 <span data-ttu-id="f0c3a-105">Normalmente, todos os campos de uma instância de objeto são serializados, que significa que os dados são representados nos dados serializados para a instância.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-105">Normally, all fields of an object instance are serialized, meaning that data is represented in the serialized data for the instance.</span></span> <span data-ttu-id="f0c3a-106">É possível para o código que pode interpretar o formato para determinar quais os valores de dados, independentemente da acessibilidade do membro.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-106">It is possible for code that can interpret the format to determine what the data values are, independent of the accessibility of the member.</span></span> <span data-ttu-id="f0c3a-107">Da mesma forma, a desserialização extrai dados da representação serializada e define o estado de objeto diretamente, novamente, independentemente de regras de acessibilidade.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-107">Similarly, deserialization extracts data from the serialized representation and sets object state directly, again irrespective of accessibility rules.</span></span>  
  
 <span data-ttu-id="f0c3a-108">Qualquer objeto que pode conter dados confidenciais de segurança deve ser feito não serializáveis, se possível.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-108">Any object that could contain security-sensitive data should be made nonserializable, if possible.</span></span> <span data-ttu-id="f0c3a-109">Se ele deve ser serializável, tente fazer a campos específicos que contêm dados confidenciais não serializável.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-109">If it must be serializable, try to make specific fields that hold sensitive data nonserializable.</span></span> <span data-ttu-id="f0c3a-110">Se isso não pode ser feito, lembre-se de que esses dados serão expostos em qualquer código que tem permissão para serializar e certifique-se de que nenhum código mal-intencionado pode obter essa permissão.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-110">If this cannot be done, be aware that this data will be exposed to any code that has permission to serialize, and make sure that no malicious code can get this permission.</span></span>  
  
 <span data-ttu-id="f0c3a-111">O <xref:System.Runtime.Serialization.ISerializable> interface destina para uso apenas pela infraestrutura de serialização.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-111">The <xref:System.Runtime.Serialization.ISerializable> interface is intended for use only by the serialization infrastructure.</span></span> <span data-ttu-id="f0c3a-112">No entanto, se desprotegido, ele pode liberar potencialmente informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-112">However, if unprotected, it can potentially release sensitive information.</span></span> <span data-ttu-id="f0c3a-113">Se você fornecer serialização personalizada implementando **ISerializable**, certifique-se de tomar as seguintes precauções:</span><span class="sxs-lookup"><span data-stu-id="f0c3a-113">If you provide custom serialization by implementing **ISerializable**, make sure you take the following precautions:</span></span>  
  
- <span data-ttu-id="f0c3a-114">O <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> método deve ser explicitamente protegido por mais exigentes de **SecurityPermission** com **SerializationFormatter** permissão especificada ou pela certificando-se de que nenhum minúsculas informações são liberadas com a saída do método.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-114">The <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> method should be explicitly secured either by demanding the **SecurityPermission** with **SerializationFormatter** permission specified or by making sure that no sensitive information is released with the method output.</span></span> <span data-ttu-id="f0c3a-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f0c3a-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="f0c3a-116">O construtor especial usado para serialização também deve executar a validação completa de entrada e deve ser protegida ou privada para ajudar a proteger contra uso indevido pelo código mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-116">The special constructor used for serialization should also perform thorough input validation and should be either protected or private to help protect against misuse by malicious code.</span></span> <span data-ttu-id="f0c3a-117">Ele deve aplicar o mesmo verificações de segurança e as permissões necessárias para obter uma instância dessa classe por outros meios, como criar explicitamente a classe ou indiretamente criá-lo por meio de algum tipo de fábrica.</span><span class="sxs-lookup"><span data-stu-id="f0c3a-117">It should enforce the same security checks and permissions required to obtain an instance of such a class by any other means, such as explicitly creating the class or indirectly creating it through some kind of factory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c3a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0c3a-118">See also</span></span>

- [<span data-ttu-id="f0c3a-119">Diretrizes de codificação segura</span><span class="sxs-lookup"><span data-stu-id="f0c3a-119">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
