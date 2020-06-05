---
title: "'<interfacename>.<membername>' já é implementado pela classe base '<baseclassname>'. Reimplementação de <type> assumido"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 6525ae08b90cc530a8f6a469d35d9ab8c27fb5e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402818"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="34481-103">'\<interfacename>.\<membername>' já é implementado pela classe base '\<baseclassname>'.</span><span class="sxs-lookup"><span data-stu-id="34481-103">'\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="34481-104">Reimplementação de \<type> assumido</span><span class="sxs-lookup"><span data-stu-id="34481-104">Re-implementation of \<type> assumed</span></span>
<span data-ttu-id="34481-105">Uma propriedade, um procedimento ou um evento em uma classe derivada usa uma `Implements` cláusula que especifica um membro de interface que já está implementado na classe base.</span><span class="sxs-lookup"><span data-stu-id="34481-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="34481-106">Uma classe derivada pode reimplementar um membro de interface que é implementado por sua classe base.</span><span class="sxs-lookup"><span data-stu-id="34481-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="34481-107">Isso não é o mesmo que substituir a implementação da classe base.</span><span class="sxs-lookup"><span data-stu-id="34481-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="34481-108">Para obter mais informações, consulte [Implements](../statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="34481-108">For more information, see [Implements](../statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="34481-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="34481-109">By default, this message is a warning.</span></span> <span data-ttu-id="34481-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="34481-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="34481-111">**ID do erro:** BC42015</span><span class="sxs-lookup"><span data-stu-id="34481-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="34481-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="34481-112">To correct this error</span></span>  
  
- <span data-ttu-id="34481-113">Se você pretende reimplementar o membro da interface, não precisa realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="34481-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="34481-114">O código em sua classe derivada acessa o membro reimplementado, a menos que você use a `MyBase` palavra-chave para acessar a implementação da classe base.</span><span class="sxs-lookup"><span data-stu-id="34481-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
- <span data-ttu-id="34481-115">Se você não pretende reimplementar o membro da interface, remova a `Implements` cláusula da propriedade, do procedimento ou da declaração de evento.</span><span class="sxs-lookup"><span data-stu-id="34481-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34481-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="34481-116">See also</span></span>

- [<span data-ttu-id="34481-117">Interfaces</span><span class="sxs-lookup"><span data-stu-id="34481-117">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
