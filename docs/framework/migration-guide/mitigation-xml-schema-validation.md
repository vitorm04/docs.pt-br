---
title: 'Mitigação: Validação do esquema XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbeeecda3bd34f5eb651cb32246f8b56d5705002
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651000"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="6c695-102">Mitigação: Validação do esquema XML</span><span class="sxs-lookup"><span data-stu-id="6c695-102">Mitigation: XML Schema Validation</span></span>
<span data-ttu-id="6c695-103">No [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], a validação do esquema XSD detectará uma violação da restrição exclusiva se uma chave composta for usada e uma chave estiver vazia.</span><span class="sxs-lookup"><span data-stu-id="6c695-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="6c695-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="6c695-104">Impact</span></span>  
 <span data-ttu-id="6c695-105">O impacto dessa alteração deve ser mínimo: com base na especificação do esquema, um erro de validação do esquema será esperado se `xsd:unique` for violado usando uma chave composta com uma chave vazia.</span><span class="sxs-lookup"><span data-stu-id="6c695-105">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="6c695-106">Redução</span><span class="sxs-lookup"><span data-stu-id="6c695-106">Mitigation</span></span>  
 <span data-ttu-id="6c695-107">Se um erro de validação do esquema for detectado se uma chave composta tiver uma chave vazia, é um recurso configurável:</span><span class="sxs-lookup"><span data-stu-id="6c695-107">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
-   <span data-ttu-id="6c695-108">Começando com os aplicativos que se destinam ao [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], a detecção do erro de validação do esquema é habilitada por padrão; no entanto, é possível recusá-la para que o erro de validação do esquema não seja detectado.</span><span class="sxs-lookup"><span data-stu-id="6c695-108">Starting with the apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
-   <span data-ttu-id="6c695-109">Em aplicativos que são executado no [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], mas se destinam ao [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] e versões anteriores, um erro de validação do esquema não é detectado por padrão; no entanto, é possível aceitá-lo para que o erro de validação do esquema seja detectado.</span><span class="sxs-lookup"><span data-stu-id="6c695-109">In apps that run under the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] but target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="6c695-110">Esse comportamento pode ser configurado usando a classe <xref:System.AppContext> para definir o valor da opção `System.Xml.IgnoreEmptyKeySequences`.</span><span class="sxs-lookup"><span data-stu-id="6c695-110">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="6c695-111">Como o valor padrão da opção é `false` (sequências de chaves vazias não são ignoradas), os aplicativos que se destinam ao [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] podem recusar o comportamento usando o seguinte código para definir o valor da opção como `true`:</span><span class="sxs-lookup"><span data-stu-id="6c695-111">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="6c695-112">Para aplicativos que se destinam ao [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] e às versões anteriores, como o valor padrão da opção é `true` (sequências de chaves vazias são ignoradas), é possível garantir que uma chave composta com uma chave vazia gere um erro de validação do esquema usando o código a seguir para definir o valor da opção como `false`.</span><span class="sxs-lookup"><span data-stu-id="6c695-112">For apps that target the [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6c695-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c695-113">See also</span></span>
- [<span data-ttu-id="6c695-114">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="6c695-114">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
