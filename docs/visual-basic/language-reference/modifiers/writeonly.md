---
title: WriteOnly
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: a9fa0a3a23561215d6ff122bc8e609b68ca6fc30
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386628"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="dd5a0-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd5a0-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="dd5a0-103">Especifica que uma propriedade pode ser gravada, mas não lida.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd5a0-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="dd5a0-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="dd5a0-105">Regras</span><span class="sxs-lookup"><span data-stu-id="dd5a0-105">Rules</span></span>  
 <span data-ttu-id="dd5a0-106">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="dd5a0-106">**Declaration Context.**</span></span> <span data-ttu-id="dd5a0-107">Você pode usar `WriteOnly` somente no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="dd5a0-108">Isso significa que o contexto de declaração para uma `WriteOnly` propriedade deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="dd5a0-109">Você pode declarar uma propriedade como `WriteOnly` , mas não uma variável.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="dd5a0-110">Quando usar WriteOnly</span><span class="sxs-lookup"><span data-stu-id="dd5a0-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="dd5a0-111">Às vezes, você quer que o código de consumo seja capaz de definir um valor, mas não descobrir o que ele é.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="dd5a0-112">Por exemplo, dados confidenciais, como um número de registro social ou uma senha, precisam ser protegidos do acesso por qualquer componente que não o definiu.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="dd5a0-113">Nesses casos, você pode usar uma `WriteOnly` propriedade para definir o valor.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dd5a0-114">Ao definir e usar uma `WriteOnly` propriedade, considere as seguintes medidas de proteção adicionais:</span><span class="sxs-lookup"><span data-stu-id="dd5a0-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="dd5a0-115">**Sobrecarga.**</span><span class="sxs-lookup"><span data-stu-id="dd5a0-115">**Overriding.**</span></span> <span data-ttu-id="dd5a0-116">Se a propriedade for um membro de uma classe, permita que ela seja padronizada como não [substituível](notoverridable.md)e não a declare `Overridable` ou `MustOverride` .</span><span class="sxs-lookup"><span data-stu-id="dd5a0-116">If the property is a member of a class, allow it to default to [NotOverridable](notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="dd5a0-117">Isso impede que uma classe derivada faça acesso indesejado por meio de uma substituição.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="dd5a0-118">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="dd5a0-118">**Access Level.**</span></span> <span data-ttu-id="dd5a0-119">Se você mantiver os dados confidenciais da propriedade em uma ou mais variáveis, declare-as como [particulares](private.md) para que nenhum outro código possa acessá-las.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-119">If you hold the property's sensitive data in one or more variables, declare them [Private](private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="dd5a0-120">**Encripta.**</span><span class="sxs-lookup"><span data-stu-id="dd5a0-120">**Encryption.**</span></span> <span data-ttu-id="dd5a0-121">Armazene todos os dados confidenciais em formato criptografado em vez de em texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="dd5a0-122">Se um código mal-intencionado tiver acesso a essa área de memória, será mais difícil fazer o uso dos dados.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="dd5a0-123">A criptografia também é útil se for necessário serializar os dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="dd5a0-124">**Redefinir.**</span><span class="sxs-lookup"><span data-stu-id="dd5a0-124">**Resetting.**</span></span> <span data-ttu-id="dd5a0-125">Quando a classe, a estrutura ou o módulo que define a propriedade está sendo encerrado, redefina os dados confidenciais para valores padrão ou para outros valores sem sentido.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="dd5a0-126">Isso fornece proteção extra quando essa área de memória é liberada para acesso geral.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="dd5a0-127">**Persistência.**</span><span class="sxs-lookup"><span data-stu-id="dd5a0-127">**Persistence.**</span></span> <span data-ttu-id="dd5a0-128">Não persista nenhum dado confidencial, por exemplo, no disco, se você puder evitá-lo.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="dd5a0-129">Além disso, não grave nenhum dado confidencial na área de transferência.</span><span class="sxs-lookup"><span data-stu-id="dd5a0-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="dd5a0-130">O `WriteOnly` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="dd5a0-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="dd5a0-131">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="dd5a0-131">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="dd5a0-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd5a0-132">See also</span></span>

- [<span data-ttu-id="dd5a0-133">Leitura</span><span class="sxs-lookup"><span data-stu-id="dd5a0-133">ReadOnly</span></span>](readonly.md)
- [<span data-ttu-id="dd5a0-134">Privada</span><span class="sxs-lookup"><span data-stu-id="dd5a0-134">Private</span></span>](private.md)
- [<span data-ttu-id="dd5a0-135">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="dd5a0-135">Keywords</span></span>](../keywords/index.md)
