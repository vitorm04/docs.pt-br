---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dab9115c31e538bd28583b9f0591ae0c9611e2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="c8b06-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8b06-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="c8b06-103">Especifica que uma propriedade pode ser gravada mas não lida.</span><span class="sxs-lookup"><span data-stu-id="c8b06-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8b06-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8b06-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c8b06-105">Regras</span><span class="sxs-lookup"><span data-stu-id="c8b06-105">Rules</span></span>  
 <span data-ttu-id="c8b06-106">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="c8b06-106">**Declaration Context.**</span></span> <span data-ttu-id="c8b06-107">Você pode usar `WriteOnly` apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="c8b06-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="c8b06-108">Isso significa que o contexto da declaração para um `WriteOnly` propriedade deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="c8b06-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="c8b06-109">Você pode declarar uma propriedade como `WriteOnly`, mas não uma variável.</span><span class="sxs-lookup"><span data-stu-id="c8b06-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="c8b06-110">Quando usar WriteOnly</span><span class="sxs-lookup"><span data-stu-id="c8b06-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="c8b06-111">Às vezes você deseja ser capaz de definir um valor, mas não descobrir o que é o código.</span><span class="sxs-lookup"><span data-stu-id="c8b06-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="c8b06-112">Por exemplo, dados confidenciais, como um número de registro social ou uma senha, precisam ser protegidos contra o acesso por qualquer componente que não definido.</span><span class="sxs-lookup"><span data-stu-id="c8b06-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="c8b06-113">Nesses casos, você pode usar um `WriteOnly` propriedade para definir o valor.</span><span class="sxs-lookup"><span data-stu-id="c8b06-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c8b06-114">Quando você definir e usar um `WriteOnly` propriedade, considere as seguintes medidas de proteção adicionais:</span><span class="sxs-lookup"><span data-stu-id="c8b06-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
-   <span data-ttu-id="c8b06-115">**Substituindo.**</span><span class="sxs-lookup"><span data-stu-id="c8b06-115">**Overriding.**</span></span> <span data-ttu-id="c8b06-116">Se a propriedade for um membro de uma classe, permitir que ele seja padrão [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)e não o declare `Overridable` ou `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="c8b06-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="c8b06-117">Isso impede que uma classe derivada faça um acesso indesejado através de uma substituição.</span><span class="sxs-lookup"><span data-stu-id="c8b06-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
-   <span data-ttu-id="c8b06-118">**Nível de acesso.**</span><span class="sxs-lookup"><span data-stu-id="c8b06-118">**Access Level.**</span></span> <span data-ttu-id="c8b06-119">Se você mantiver dados confidenciais a propriedade em uma ou mais variáveis, declare-los [privada](../../../visual-basic/language-reference/modifiers/private.md) para que nenhum outro código possa acessá-los.</span><span class="sxs-lookup"><span data-stu-id="c8b06-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
-   <span data-ttu-id="c8b06-120">**Criptografia.**</span><span class="sxs-lookup"><span data-stu-id="c8b06-120">**Encryption.**</span></span> <span data-ttu-id="c8b06-121">Armazene todos os dados confidenciais em formato criptografado em vez de em texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="c8b06-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="c8b06-122">Se alguma forma, o código mal-intencionado obtiver acesso a área da memória, é mais difícil fazer uso dos dados.</span><span class="sxs-lookup"><span data-stu-id="c8b06-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="c8b06-123">A criptografia também é útil se for necessário serializar os dados confidenciais.</span><span class="sxs-lookup"><span data-stu-id="c8b06-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
-   <span data-ttu-id="c8b06-124">**A redefinição.**</span><span class="sxs-lookup"><span data-stu-id="c8b06-124">**Resetting.**</span></span> <span data-ttu-id="c8b06-125">Quando a classe, estrutura ou módulo definindo a propriedade está sendo finalizado, redefina os dados confidenciais para valores padrão ou outros valores sem sentido.</span><span class="sxs-lookup"><span data-stu-id="c8b06-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="c8b06-126">Isso proporciona proteção extra quando essa área da memória é liberada para acesso geral.</span><span class="sxs-lookup"><span data-stu-id="c8b06-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
-   <span data-ttu-id="c8b06-127">**Persistência.**</span><span class="sxs-lookup"><span data-stu-id="c8b06-127">**Persistence.**</span></span> <span data-ttu-id="c8b06-128">Não mantenha quaisquer dados confidenciais, por exemplo, no disco, se for possível evitar.</span><span class="sxs-lookup"><span data-stu-id="c8b06-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="c8b06-129">Além disso, não grave dados confidenciais na área de transferência.</span><span class="sxs-lookup"><span data-stu-id="c8b06-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="c8b06-130">O `WriteOnly` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="c8b06-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="c8b06-131">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="c8b06-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c8b06-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8b06-132">See Also</span></span>  
 [<span data-ttu-id="c8b06-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="c8b06-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="c8b06-134">Privado</span><span class="sxs-lookup"><span data-stu-id="c8b06-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="c8b06-135">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c8b06-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
