---
title: "Coleções de esquema de banco de dados OLE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e120ea532b6da455e31ce7345b6c4b2be1ec975f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="c54e9-102">Coleções de esquema de banco de dados OLE</span><span class="sxs-lookup"><span data-stu-id="c54e9-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="c54e9-103">Esta seção discute o suporte de coleção de esquema para os provedores OLE DB para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="c54e9-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="c54e9-104">Provedor Microsoft SQL Server, OLE DB</span><span class="sxs-lookup"><span data-stu-id="c54e9-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="c54e9-105">O Microsoft OLE DB Driver do SQL Server suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="c54e9-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c54e9-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="c54e9-106">Tables</span></span>  
  
-   <span data-ttu-id="c54e9-107">Colunas</span><span class="sxs-lookup"><span data-stu-id="c54e9-107">Columns</span></span>  
  
-   <span data-ttu-id="c54e9-108">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c54e9-108">Procedures</span></span>  
  
-   <span data-ttu-id="c54e9-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c54e9-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="c54e9-110">Catálogo</span><span class="sxs-lookup"><span data-stu-id="c54e9-110">Catalog</span></span>  
  
-   <span data-ttu-id="c54e9-111">Índices</span><span class="sxs-lookup"><span data-stu-id="c54e9-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="c54e9-112">Tabelas</span><span class="sxs-lookup"><span data-stu-id="c54e9-112">Tables</span></span>  
  
|<span data-ttu-id="c54e9-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-113">ColumnName</span></span>|<span data-ttu-id="c54e9-114">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-115">TABLE_CATALOG</span></span>|<span data-ttu-id="c54e9-116">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-116">String</span></span>|  
|<span data-ttu-id="c54e9-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="c54e9-118">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-118">String</span></span>|  
|<span data-ttu-id="c54e9-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-119">TABLE_NAME</span></span>|<span data-ttu-id="c54e9-120">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-120">String</span></span>|  
|<span data-ttu-id="c54e9-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c54e9-121">TABLE_TYPE</span></span>|<span data-ttu-id="c54e9-122">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-122">String</span></span>|  
|<span data-ttu-id="c54e9-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-123">TABLE_GUID</span></span>|<span data-ttu-id="c54e9-124">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-124">Guid</span></span>|  
|<span data-ttu-id="c54e9-125">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-125">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-126">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-126">String</span></span>|  
|<span data-ttu-id="c54e9-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="c54e9-127">TABLE_PROPID</span></span>|<span data-ttu-id="c54e9-128">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-128">Int64</span></span>|  
|<span data-ttu-id="c54e9-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="c54e9-129">DATE_CREATED</span></span>|<span data-ttu-id="c54e9-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-130">DateTime</span></span>|  
|<span data-ttu-id="c54e9-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="c54e9-131">DATE_MODIFIED</span></span>|<span data-ttu-id="c54e9-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c54e9-133">Colunas</span><span class="sxs-lookup"><span data-stu-id="c54e9-133">Columns</span></span>  
  
|<span data-ttu-id="c54e9-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-134">ColumnName</span></span>|<span data-ttu-id="c54e9-135">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-136">TABLE_CATALOG</span></span>|<span data-ttu-id="c54e9-137">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-137">String</span></span>|  
|<span data-ttu-id="c54e9-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="c54e9-139">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-139">String</span></span>|  
|<span data-ttu-id="c54e9-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-140">TABLE_NAME</span></span>|<span data-ttu-id="c54e9-141">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-141">String</span></span>|  
|<span data-ttu-id="c54e9-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-142">COLUMN_NAME</span></span>|<span data-ttu-id="c54e9-143">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-143">String</span></span>|  
|<span data-ttu-id="c54e9-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-144">COLUMN_GUID</span></span>|<span data-ttu-id="c54e9-145">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-145">Guid</span></span>|  
|<span data-ttu-id="c54e9-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="c54e9-146">COLUMN_PROPID</span></span>|<span data-ttu-id="c54e9-147">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-147">Int64</span></span>|  
|<span data-ttu-id="c54e9-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="c54e9-149">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-149">Int64</span></span>|  
|<span data-ttu-id="c54e9-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="c54e9-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="c54e9-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-151">Boolean</span></span>|  
|<span data-ttu-id="c54e9-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c54e9-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="c54e9-153">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-153">String</span></span>|  
|<span data-ttu-id="c54e9-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="c54e9-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="c54e9-155">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-155">Int64</span></span>|  
|<span data-ttu-id="c54e9-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c54e9-156">IS_NULLABLE</span></span>|<span data-ttu-id="c54e9-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-157">Boolean</span></span>|  
|<span data-ttu-id="c54e9-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c54e9-158">DATA_TYPE</span></span>|<span data-ttu-id="c54e9-159">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-159">Int32</span></span>|  
|<span data-ttu-id="c54e9-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-160">TYPE_GUID</span></span>|<span data-ttu-id="c54e9-161">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-161">Guid</span></span>|  
|<span data-ttu-id="c54e9-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c54e9-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="c54e9-163">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-163">Int64</span></span>|  
|<span data-ttu-id="c54e9-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c54e9-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="c54e9-165">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-165">Int64</span></span>|  
|<span data-ttu-id="c54e9-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="c54e9-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="c54e9-167">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-167">Int32</span></span>|  
|<span data-ttu-id="c54e9-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="c54e9-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="c54e9-169">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-169">Int16</span></span>|  
|<span data-ttu-id="c54e9-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="c54e9-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="c54e9-171">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-171">Int64</span></span>|  
|<span data-ttu-id="c54e9-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="c54e9-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-173">String</span></span>|  
|<span data-ttu-id="c54e9-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="c54e9-175">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-175">String</span></span>|  
|<span data-ttu-id="c54e9-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="c54e9-177">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-177">String</span></span>|  
|<span data-ttu-id="c54e9-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="c54e9-179">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-179">String</span></span>|  
|<span data-ttu-id="c54e9-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="c54e9-181">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-181">String</span></span>|  
|<span data-ttu-id="c54e9-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-182">COLLATION_NAME</span></span>|<span data-ttu-id="c54e9-183">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-183">String</span></span>|  
|<span data-ttu-id="c54e9-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="c54e9-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-185">String</span></span>|  
|<span data-ttu-id="c54e9-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="c54e9-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-187">String</span></span>|  
|<span data-ttu-id="c54e9-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-188">DOMAIN_NAME</span></span>|<span data-ttu-id="c54e9-189">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-189">String</span></span>|  
|<span data-ttu-id="c54e9-190">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-190">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-191">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-191">String</span></span>|  
|<span data-ttu-id="c54e9-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="c54e9-192">COLUMN_LCID</span></span>|<span data-ttu-id="c54e9-193">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-193">Int32</span></span>|  
|<span data-ttu-id="c54e9-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="c54e9-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="c54e9-195">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-195">Int32</span></span>|  
|<span data-ttu-id="c54e9-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="c54e9-196">COLUMN_SORTID</span></span>|<span data-ttu-id="c54e9-197">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-197">Int32</span></span>|  
|<span data-ttu-id="c54e9-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="c54e9-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="c54e9-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="c54e9-199">Byte[]</span></span>|  
|<span data-ttu-id="c54e9-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="c54e9-200">IS_COMPUTED</span></span>|<span data-ttu-id="c54e9-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c54e9-202">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c54e9-202">Procedures</span></span>  
  
|<span data-ttu-id="c54e9-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-203">ColumnName</span></span>|<span data-ttu-id="c54e9-204">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="c54e9-206">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-206">String</span></span>|  
|<span data-ttu-id="c54e9-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="c54e9-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-208">String</span></span>|  
|<span data-ttu-id="c54e9-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="c54e9-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-210">String</span></span>|  
|<span data-ttu-id="c54e9-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c54e9-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c54e9-212">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-212">Int16</span></span>|  
|<span data-ttu-id="c54e9-213">DEFINIÇÃO_DO_PROCEDIMENTO</span><span class="sxs-lookup"><span data-stu-id="c54e9-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="c54e9-214">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-214">String</span></span>|  
|<span data-ttu-id="c54e9-215">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-215">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-216">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-216">String</span></span>|  
|<span data-ttu-id="c54e9-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="c54e9-217">DATE_CREATED</span></span>|<span data-ttu-id="c54e9-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-218">DateTime</span></span>|  
|<span data-ttu-id="c54e9-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="c54e9-219">DATE_MODIFIED</span></span>|<span data-ttu-id="c54e9-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="c54e9-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c54e9-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="c54e9-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-222">ColumnName</span></span>|<span data-ttu-id="c54e9-223">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="c54e9-225">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-225">String</span></span>|  
|<span data-ttu-id="c54e9-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="c54e9-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-227">String</span></span>|  
|<span data-ttu-id="c54e9-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="c54e9-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-229">String</span></span>|  
|<span data-ttu-id="c54e9-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-230">PARAMETER_NAME</span></span>|<span data-ttu-id="c54e9-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-231">String</span></span>|  
|<span data-ttu-id="c54e9-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="c54e9-233">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-233">Int32</span></span>|  
|<span data-ttu-id="c54e9-234">TIPO_DE_PARÂMETRO</span><span class="sxs-lookup"><span data-stu-id="c54e9-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="c54e9-235">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-235">Int32</span></span>|  
|<span data-ttu-id="c54e9-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="c54e9-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="c54e9-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-237">Boolean</span></span>|  
|<span data-ttu-id="c54e9-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c54e9-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="c54e9-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-239">String</span></span>|  
|<span data-ttu-id="c54e9-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c54e9-240">IS_NULLABLE</span></span>|<span data-ttu-id="c54e9-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-241">Boolean</span></span>|  
|<span data-ttu-id="c54e9-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c54e9-242">DATA_TYPE</span></span>|<span data-ttu-id="c54e9-243">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-243">Int32</span></span>|  
|<span data-ttu-id="c54e9-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c54e9-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="c54e9-245">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-245">Int64</span></span>|  
|<span data-ttu-id="c54e9-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c54e9-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="c54e9-247">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-247">Int64</span></span>|  
|<span data-ttu-id="c54e9-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="c54e9-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="c54e9-249">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-249">Int32</span></span>|  
|<span data-ttu-id="c54e9-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="c54e9-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="c54e9-251">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-251">Int16</span></span>|  
|<span data-ttu-id="c54e9-252">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-252">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-253">String</span></span>|  
|<span data-ttu-id="c54e9-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-254">TYPE_NAME</span></span>|<span data-ttu-id="c54e9-255">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-255">String</span></span>|  
|<span data-ttu-id="c54e9-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="c54e9-257">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="c54e9-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="c54e9-258">Catalog</span></span>  
  
|<span data-ttu-id="c54e9-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-259">ColumnName</span></span>|<span data-ttu-id="c54e9-260">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-261">CATALOG_NAME</span></span>|<span data-ttu-id="c54e9-262">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-262">String</span></span>|  
|<span data-ttu-id="c54e9-263">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-263">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-264">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="c54e9-265">Índices</span><span class="sxs-lookup"><span data-stu-id="c54e9-265">Indexes</span></span>  
  
|<span data-ttu-id="c54e9-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-266">ColumnName</span></span>|<span data-ttu-id="c54e9-267">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-268">TABLE_CATALOG</span></span>|<span data-ttu-id="c54e9-269">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-269">String</span></span>|  
|<span data-ttu-id="c54e9-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="c54e9-271">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-271">String</span></span>|  
|<span data-ttu-id="c54e9-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-272">TABLE_NAME</span></span>|<span data-ttu-id="c54e9-273">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-273">String</span></span>|  
|<span data-ttu-id="c54e9-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-274">INDEX_CATALOG</span></span>|<span data-ttu-id="c54e9-275">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-275">String</span></span>|  
|<span data-ttu-id="c54e9-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="c54e9-277">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-277">String</span></span>|  
|<span data-ttu-id="c54e9-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-278">INDEX_NAME</span></span>|<span data-ttu-id="c54e9-279">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-279">String</span></span>|  
|<span data-ttu-id="c54e9-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="c54e9-280">PRIMARY_KEY</span></span>|<span data-ttu-id="c54e9-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-281">Boolean</span></span>|  
|<span data-ttu-id="c54e9-282">EXCLUSIVO</span><span class="sxs-lookup"><span data-stu-id="c54e9-282">UNIQUE</span></span>|<span data-ttu-id="c54e9-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-283">Boolean</span></span>|  
|<span data-ttu-id="c54e9-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="c54e9-284">CLUSTERED</span></span>|<span data-ttu-id="c54e9-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-285">Boolean</span></span>|  
|<span data-ttu-id="c54e9-286">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="c54e9-286">TYPE</span></span>|<span data-ttu-id="c54e9-287">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-287">Int32</span></span>|  
|<span data-ttu-id="c54e9-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="c54e9-288">FILL_FACTOR</span></span>|<span data-ttu-id="c54e9-289">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-289">Int32</span></span>|  
|<span data-ttu-id="c54e9-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="c54e9-290">INITIAL_SIZE</span></span>|<span data-ttu-id="c54e9-291">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-291">Int32</span></span>|  
|<span data-ttu-id="c54e9-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="c54e9-292">NULLS</span></span>|<span data-ttu-id="c54e9-293">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-293">Int32</span></span>|  
|<span data-ttu-id="c54e9-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="c54e9-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="c54e9-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-295">Boolean</span></span>|  
|<span data-ttu-id="c54e9-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="c54e9-296">AUTO_UPDATE</span></span>|<span data-ttu-id="c54e9-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-297">Boolean</span></span>|  
|<span data-ttu-id="c54e9-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="c54e9-298">NULL_COLLATION</span></span>|<span data-ttu-id="c54e9-299">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-299">Int32</span></span>|  
|<span data-ttu-id="c54e9-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="c54e9-301">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-301">Int64</span></span>|  
|<span data-ttu-id="c54e9-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-302">COLUMN_NAME</span></span>|<span data-ttu-id="c54e9-303">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-303">String</span></span>|  
|<span data-ttu-id="c54e9-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-304">COLUMN_GUID</span></span>|<span data-ttu-id="c54e9-305">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-305">Guid</span></span>|  
|<span data-ttu-id="c54e9-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="c54e9-306">COLUMN_PROPID</span></span>|<span data-ttu-id="c54e9-307">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-307">Int64</span></span>|  
|<span data-ttu-id="c54e9-308">AGRUPAMENTO</span><span class="sxs-lookup"><span data-stu-id="c54e9-308">COLLATION</span></span>|<span data-ttu-id="c54e9-309">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-309">Int16</span></span>|  
|<span data-ttu-id="c54e9-310">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="c54e9-310">CARDINALITY</span></span>|<span data-ttu-id="c54e9-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="c54e9-311">Decimal</span></span>|  
|<span data-ttu-id="c54e9-312">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="c54e9-312">PAGES</span></span>|<span data-ttu-id="c54e9-313">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-313">Int32</span></span>|  
|<span data-ttu-id="c54e9-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-314">FILTER_CONDITION</span></span>|<span data-ttu-id="c54e9-315">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-315">String</span></span>|  
|<span data-ttu-id="c54e9-316">INTEGRADO</span><span class="sxs-lookup"><span data-stu-id="c54e9-316">INTEGRATED</span></span>|<span data-ttu-id="c54e9-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="c54e9-318">Provedor OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="c54e9-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="c54e9-319">O Microsoft OLE DB Driver Oracle suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="c54e9-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c54e9-320">Tabelas</span><span class="sxs-lookup"><span data-stu-id="c54e9-320">Tables</span></span>  
  
-   <span data-ttu-id="c54e9-321">Colunas</span><span class="sxs-lookup"><span data-stu-id="c54e9-321">Columns</span></span>  
  
-   <span data-ttu-id="c54e9-322">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c54e9-322">Procedures</span></span>  
  
-   <span data-ttu-id="c54e9-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c54e9-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="c54e9-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c54e9-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="c54e9-325">Exibições</span><span class="sxs-lookup"><span data-stu-id="c54e9-325">Views</span></span>  
  
-   <span data-ttu-id="c54e9-326">Índices</span><span class="sxs-lookup"><span data-stu-id="c54e9-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="c54e9-327">Tabelas</span><span class="sxs-lookup"><span data-stu-id="c54e9-327">Tables</span></span>  
  
|<span data-ttu-id="c54e9-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-328">ColumnName</span></span>|<span data-ttu-id="c54e9-329">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-330">TABLE_CATALOG</span></span>|<span data-ttu-id="c54e9-331">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-331">String</span></span>|  
|<span data-ttu-id="c54e9-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="c54e9-333">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-333">String</span></span>|  
|<span data-ttu-id="c54e9-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-334">TABLE_NAME</span></span>|<span data-ttu-id="c54e9-335">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-335">String</span></span>|  
|<span data-ttu-id="c54e9-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c54e9-336">TABLE_TYPE</span></span>|<span data-ttu-id="c54e9-337">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-337">String</span></span>|  
|<span data-ttu-id="c54e9-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-338">TABLE_GUID</span></span>|<span data-ttu-id="c54e9-339">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-339">Guid</span></span>|  
|<span data-ttu-id="c54e9-340">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-340">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-341">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-341">String</span></span>|  
|<span data-ttu-id="c54e9-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="c54e9-342">TABLE_PROPID</span></span>|<span data-ttu-id="c54e9-343">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-343">Int64</span></span>|  
|<span data-ttu-id="c54e9-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="c54e9-344">DATE_CREATED</span></span>|<span data-ttu-id="c54e9-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-345">DateTime</span></span>|  
|<span data-ttu-id="c54e9-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="c54e9-346">DATE_MODIFIED</span></span>|<span data-ttu-id="c54e9-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c54e9-348">Colunas</span><span class="sxs-lookup"><span data-stu-id="c54e9-348">Columns</span></span>  
  
|<span data-ttu-id="c54e9-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-349">ColumnName</span></span>|<span data-ttu-id="c54e9-350">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-351">TABLE_CATALOG</span></span>|<span data-ttu-id="c54e9-352">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-352">String</span></span>|  
|<span data-ttu-id="c54e9-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="c54e9-354">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-354">String</span></span>|  
|<span data-ttu-id="c54e9-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-355">TABLE_NAME</span></span>|<span data-ttu-id="c54e9-356">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-356">String</span></span>|  
|<span data-ttu-id="c54e9-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-357">COLUMN_NAME</span></span>|<span data-ttu-id="c54e9-358">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-358">String</span></span>|  
|<span data-ttu-id="c54e9-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-359">COLUMN_GUID</span></span>|<span data-ttu-id="c54e9-360">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-360">Guid</span></span>|  
|<span data-ttu-id="c54e9-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="c54e9-361">COLUMN_PROPID</span></span>|<span data-ttu-id="c54e9-362">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-362">Int64</span></span>|  
|<span data-ttu-id="c54e9-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="c54e9-364">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-364">Int64</span></span>|  
|<span data-ttu-id="c54e9-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="c54e9-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="c54e9-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-366">Boolean</span></span>|  
|<span data-ttu-id="c54e9-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c54e9-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="c54e9-368">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-368">String</span></span>|  
|<span data-ttu-id="c54e9-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="c54e9-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="c54e9-370">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-370">Int64</span></span>|  
|<span data-ttu-id="c54e9-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c54e9-371">IS_NULLABLE</span></span>|<span data-ttu-id="c54e9-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-372">Boolean</span></span>|  
|<span data-ttu-id="c54e9-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c54e9-373">DATA_TYPE</span></span>|<span data-ttu-id="c54e9-374">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-374">Int32</span></span>|  
|<span data-ttu-id="c54e9-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-375">TYPE_GUID</span></span>|<span data-ttu-id="c54e9-376">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-376">Guid</span></span>|  
|<span data-ttu-id="c54e9-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c54e9-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="c54e9-378">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-378">Int64</span></span>|  
|<span data-ttu-id="c54e9-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c54e9-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="c54e9-380">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-380">Int64</span></span>|  
|<span data-ttu-id="c54e9-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="c54e9-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="c54e9-382">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-382">Int32</span></span>|  
|<span data-ttu-id="c54e9-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="c54e9-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="c54e9-384">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-384">Int16</span></span>|  
|<span data-ttu-id="c54e9-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="c54e9-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="c54e9-386">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-386">Int64</span></span>|  
|<span data-ttu-id="c54e9-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="c54e9-388">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-388">String</span></span>|  
|<span data-ttu-id="c54e9-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="c54e9-390">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-390">String</span></span>|  
|<span data-ttu-id="c54e9-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="c54e9-392">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-392">String</span></span>|  
|<span data-ttu-id="c54e9-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="c54e9-394">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-394">String</span></span>|  
|<span data-ttu-id="c54e9-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="c54e9-396">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-396">String</span></span>|  
|<span data-ttu-id="c54e9-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-397">COLLATION_NAME</span></span>|<span data-ttu-id="c54e9-398">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-398">String</span></span>|  
|<span data-ttu-id="c54e9-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="c54e9-400">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-400">String</span></span>|  
|<span data-ttu-id="c54e9-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="c54e9-402">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-402">String</span></span>|  
|<span data-ttu-id="c54e9-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-403">DOMAIN_NAME</span></span>|<span data-ttu-id="c54e9-404">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-404">String</span></span>|  
|<span data-ttu-id="c54e9-405">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-405">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-406">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c54e9-407">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c54e9-407">Procedures</span></span>  
  
|<span data-ttu-id="c54e9-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-408">ColumnName</span></span>|<span data-ttu-id="c54e9-409">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="c54e9-411">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-411">String</span></span>|  
|<span data-ttu-id="c54e9-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="c54e9-413">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-413">String</span></span>|  
|<span data-ttu-id="c54e9-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="c54e9-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-415">String</span></span>|  
|<span data-ttu-id="c54e9-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c54e9-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c54e9-417">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-417">Int16</span></span>|  
|<span data-ttu-id="c54e9-418">DEFINIÇÃO_DO_PROCEDIMENTO</span><span class="sxs-lookup"><span data-stu-id="c54e9-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="c54e9-419">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-419">String</span></span>|  
|<span data-ttu-id="c54e9-420">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-420">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-421">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-421">String</span></span>|  
|<span data-ttu-id="c54e9-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="c54e9-422">DATE_CREATED</span></span>|<span data-ttu-id="c54e9-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-423">DateTime</span></span>|  
|<span data-ttu-id="c54e9-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="c54e9-424">DATE_MODIFIED</span></span>|<span data-ttu-id="c54e9-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="c54e9-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c54e9-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="c54e9-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-427">ColumnName</span></span>|<span data-ttu-id="c54e9-428">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="c54e9-430">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-430">String</span></span>|  
|<span data-ttu-id="c54e9-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="c54e9-432">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-432">String</span></span>|  
|<span data-ttu-id="c54e9-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="c54e9-434">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-434">String</span></span>|  
|<span data-ttu-id="c54e9-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-435">COLUMN_NAME</span></span>|<span data-ttu-id="c54e9-436">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-436">String</span></span>|  
|<span data-ttu-id="c54e9-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-437">COLUMN_GUID</span></span>|<span data-ttu-id="c54e9-438">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-438">Guid</span></span>|  
|<span data-ttu-id="c54e9-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="c54e9-439">COLUMN_PROPID</span></span>|<span data-ttu-id="c54e9-440">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-440">Int64</span></span>|  
|<span data-ttu-id="c54e9-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="c54e9-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="c54e9-442">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-442">Int64</span></span>|  
|<span data-ttu-id="c54e9-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="c54e9-444">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-444">Int64</span></span>|  
|<span data-ttu-id="c54e9-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c54e9-445">IS_NULLABLE</span></span>|<span data-ttu-id="c54e9-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-446">Boolean</span></span>|  
|<span data-ttu-id="c54e9-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c54e9-447">DATA_TYPE</span></span>|<span data-ttu-id="c54e9-448">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-448">Int32</span></span>|  
|<span data-ttu-id="c54e9-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-449">TYPE_GUID</span></span>|<span data-ttu-id="c54e9-450">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-450">Guid</span></span>|  
|<span data-ttu-id="c54e9-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c54e9-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="c54e9-452">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-452">Int64</span></span>|  
|<span data-ttu-id="c54e9-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c54e9-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="c54e9-454">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-454">Int64</span></span>|  
|<span data-ttu-id="c54e9-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="c54e9-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="c54e9-456">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-456">Int32</span></span>|  
|<span data-ttu-id="c54e9-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="c54e9-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="c54e9-458">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-458">Int16</span></span>|  
|<span data-ttu-id="c54e9-459">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-459">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-460">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-460">String</span></span>|  
|<span data-ttu-id="c54e9-461">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="c54e9-461">OVERLOAD</span></span>|<span data-ttu-id="c54e9-462">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="c54e9-463">Exibições</span><span class="sxs-lookup"><span data-stu-id="c54e9-463">Views</span></span>  
  
|<span data-ttu-id="c54e9-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-464">ColumnName</span></span>|<span data-ttu-id="c54e9-465">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-466">TABLE_CATALOG</span></span>|<span data-ttu-id="c54e9-467">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-467">String</span></span>|  
|<span data-ttu-id="c54e9-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="c54e9-469">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-469">String</span></span>|  
|<span data-ttu-id="c54e9-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-470">TABLE_NAME</span></span>|<span data-ttu-id="c54e9-471">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-471">String</span></span>|  
|<span data-ttu-id="c54e9-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="c54e9-473">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-473">String</span></span>|  
|<span data-ttu-id="c54e9-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="c54e9-474">CHECK_OPTION</span></span>|<span data-ttu-id="c54e9-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-475">Boolean</span></span>|  
|<span data-ttu-id="c54e9-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="c54e9-476">IS_UPDATABLE</span></span>|<span data-ttu-id="c54e9-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-477">Boolean</span></span>|  
|<span data-ttu-id="c54e9-478">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-478">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-479">String</span></span>|  
|<span data-ttu-id="c54e9-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="c54e9-480">DATE_CREATED</span></span>|<span data-ttu-id="c54e9-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-481">DateTime</span></span>|  
|<span data-ttu-id="c54e9-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="c54e9-482">DATE_MODIFIED</span></span>|<span data-ttu-id="c54e9-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="c54e9-484">Índices</span><span class="sxs-lookup"><span data-stu-id="c54e9-484">Indexes</span></span>  
  
|<span data-ttu-id="c54e9-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-485">ColumnName</span></span>|<span data-ttu-id="c54e9-486">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-487">TABLE_CATALOG</span></span>|<span data-ttu-id="c54e9-488">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-488">String</span></span>|  
|<span data-ttu-id="c54e9-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="c54e9-490">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-490">String</span></span>|  
|<span data-ttu-id="c54e9-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-491">TABLE_NAME</span></span>|<span data-ttu-id="c54e9-492">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-492">String</span></span>|  
|<span data-ttu-id="c54e9-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-493">INDEX_CATALOG</span></span>|<span data-ttu-id="c54e9-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-494">String</span></span>|  
|<span data-ttu-id="c54e9-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="c54e9-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-496">String</span></span>|  
|<span data-ttu-id="c54e9-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-497">INDEX_NAME</span></span>|<span data-ttu-id="c54e9-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-498">String</span></span>|  
|<span data-ttu-id="c54e9-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="c54e9-499">PRIMARY_KEY</span></span>|<span data-ttu-id="c54e9-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-500">Boolean</span></span>|  
|<span data-ttu-id="c54e9-501">EXCLUSIVO</span><span class="sxs-lookup"><span data-stu-id="c54e9-501">UNIQUE</span></span>|<span data-ttu-id="c54e9-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-502">Boolean</span></span>|  
|<span data-ttu-id="c54e9-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="c54e9-503">CLUSTERED</span></span>|<span data-ttu-id="c54e9-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-504">Boolean</span></span>|  
|<span data-ttu-id="c54e9-505">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="c54e9-505">TYPE</span></span>|<span data-ttu-id="c54e9-506">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-506">Int32</span></span>|  
|<span data-ttu-id="c54e9-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="c54e9-507">FILL_FACTOR</span></span>|<span data-ttu-id="c54e9-508">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-508">Int32</span></span>|  
|<span data-ttu-id="c54e9-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="c54e9-509">INITIAL_SIZE</span></span>|<span data-ttu-id="c54e9-510">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-510">Int32</span></span>|  
|<span data-ttu-id="c54e9-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="c54e9-511">NULLS</span></span>|<span data-ttu-id="c54e9-512">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-512">Int32</span></span>|  
|<span data-ttu-id="c54e9-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="c54e9-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="c54e9-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-514">Boolean</span></span>|  
|<span data-ttu-id="c54e9-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="c54e9-515">AUTO_UPDATE</span></span>|<span data-ttu-id="c54e9-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-516">Boolean</span></span>|  
|<span data-ttu-id="c54e9-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="c54e9-517">NULL_COLLATION</span></span>|<span data-ttu-id="c54e9-518">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-518">Int32</span></span>|  
|<span data-ttu-id="c54e9-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="c54e9-520">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-520">Int64</span></span>|  
|<span data-ttu-id="c54e9-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-521">COLUMN_NAME</span></span>|<span data-ttu-id="c54e9-522">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-522">String</span></span>|  
|<span data-ttu-id="c54e9-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-523">COLUMN_GUID</span></span>|<span data-ttu-id="c54e9-524">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-524">Guid</span></span>|  
|<span data-ttu-id="c54e9-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="c54e9-525">COLUMN_PROPID</span></span>|<span data-ttu-id="c54e9-526">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-526">Int64</span></span>|  
|<span data-ttu-id="c54e9-527">AGRUPAMENTO</span><span class="sxs-lookup"><span data-stu-id="c54e9-527">COLLATION</span></span>|<span data-ttu-id="c54e9-528">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-528">Int16</span></span>|  
|<span data-ttu-id="c54e9-529">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="c54e9-529">CARDINALITY</span></span>|<span data-ttu-id="c54e9-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="c54e9-530">Decimal</span></span>|  
|<span data-ttu-id="c54e9-531">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="c54e9-531">PAGES</span></span>|<span data-ttu-id="c54e9-532">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-532">Int32</span></span>|  
|<span data-ttu-id="c54e9-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-533">FILTER_CONDITION</span></span>|<span data-ttu-id="c54e9-534">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-534">String</span></span>|  
|<span data-ttu-id="c54e9-535">INTEGRADO</span><span class="sxs-lookup"><span data-stu-id="c54e9-535">INTEGRATED</span></span>|<span data-ttu-id="c54e9-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="c54e9-537">Provedor do Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="c54e9-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="c54e9-538">O Microsoft Jet OLE DB Driver suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="c54e9-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c54e9-539">Tabelas</span><span class="sxs-lookup"><span data-stu-id="c54e9-539">Tables</span></span>  
  
-   <span data-ttu-id="c54e9-540">Colunas</span><span class="sxs-lookup"><span data-stu-id="c54e9-540">Columns</span></span>  
  
-   <span data-ttu-id="c54e9-541">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c54e9-541">Procedures</span></span>  
  
-   <span data-ttu-id="c54e9-542">Exibições</span><span class="sxs-lookup"><span data-stu-id="c54e9-542">Views</span></span>  
  
-   <span data-ttu-id="c54e9-543">Índices</span><span class="sxs-lookup"><span data-stu-id="c54e9-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="c54e9-544">Tabelas</span><span class="sxs-lookup"><span data-stu-id="c54e9-544">Tables</span></span>  
  
|<span data-ttu-id="c54e9-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-545">ColumnName</span></span>|<span data-ttu-id="c54e9-546">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-547">TABLE_CATALOG</span></span>|<span data-ttu-id="c54e9-548">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-548">String</span></span>|  
|<span data-ttu-id="c54e9-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="c54e9-550">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-550">String</span></span>|  
|<span data-ttu-id="c54e9-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-551">TABLE_NAME</span></span>|<span data-ttu-id="c54e9-552">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-552">String</span></span>|  
|<span data-ttu-id="c54e9-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c54e9-553">TABLE_TYPE</span></span>|<span data-ttu-id="c54e9-554">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-554">String</span></span>|  
|<span data-ttu-id="c54e9-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-555">TABLE_GUID</span></span>|<span data-ttu-id="c54e9-556">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-556">Guid</span></span>|  
|<span data-ttu-id="c54e9-557">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-557">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-558">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-558">String</span></span>|  
|<span data-ttu-id="c54e9-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="c54e9-559">TABLE_PROPID</span></span>|<span data-ttu-id="c54e9-560">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-560">Int64</span></span>|  
|<span data-ttu-id="c54e9-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="c54e9-561">DATE_CREATED</span></span>|<span data-ttu-id="c54e9-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-562">DateTime</span></span>|  
|<span data-ttu-id="c54e9-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="c54e9-563">DATE_MODIFIED</span></span>|<span data-ttu-id="c54e9-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c54e9-565">Colunas</span><span class="sxs-lookup"><span data-stu-id="c54e9-565">Columns</span></span>  
  
|<span data-ttu-id="c54e9-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-566">ColumnName</span></span>|<span data-ttu-id="c54e9-567">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-568">TABLE_CATALOG</span></span>|<span data-ttu-id="c54e9-569">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-569">String</span></span>|  
|<span data-ttu-id="c54e9-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="c54e9-571">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-571">String</span></span>|  
|<span data-ttu-id="c54e9-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-572">TABLE_NAME</span></span>|<span data-ttu-id="c54e9-573">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-573">String</span></span>|  
|<span data-ttu-id="c54e9-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-574">COLUMN_NAME</span></span>|<span data-ttu-id="c54e9-575">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-575">String</span></span>|  
|<span data-ttu-id="c54e9-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-576">COLUMN_GUID</span></span>|<span data-ttu-id="c54e9-577">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-577">Guid</span></span>|  
|<span data-ttu-id="c54e9-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="c54e9-578">COLUMN_PROPID</span></span>|<span data-ttu-id="c54e9-579">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-579">Int64</span></span>|  
|<span data-ttu-id="c54e9-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="c54e9-581">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-581">Int64</span></span>|  
|<span data-ttu-id="c54e9-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="c54e9-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="c54e9-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-583">Boolean</span></span>|  
|<span data-ttu-id="c54e9-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="c54e9-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="c54e9-585">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-585">String</span></span>|  
|<span data-ttu-id="c54e9-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="c54e9-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="c54e9-587">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-587">Int64</span></span>|  
|<span data-ttu-id="c54e9-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c54e9-588">IS_NULLABLE</span></span>|<span data-ttu-id="c54e9-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-589">Boolean</span></span>|  
|<span data-ttu-id="c54e9-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c54e9-590">DATA_TYPE</span></span>|<span data-ttu-id="c54e9-591">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-591">Int32</span></span>|  
|<span data-ttu-id="c54e9-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-592">TYPE_GUID</span></span>|<span data-ttu-id="c54e9-593">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-593">Guid</span></span>|  
|<span data-ttu-id="c54e9-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c54e9-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="c54e9-595">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-595">Int64</span></span>|  
|<span data-ttu-id="c54e9-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c54e9-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="c54e9-597">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-597">Int64</span></span>|  
|<span data-ttu-id="c54e9-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="c54e9-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="c54e9-599">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-599">Int32</span></span>|  
|<span data-ttu-id="c54e9-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="c54e9-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="c54e9-601">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-601">Int16</span></span>|  
|<span data-ttu-id="c54e9-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="c54e9-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="c54e9-603">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-603">Int64</span></span>|  
|<span data-ttu-id="c54e9-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="c54e9-605">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-605">String</span></span>|  
|<span data-ttu-id="c54e9-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="c54e9-607">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-607">String</span></span>|  
|<span data-ttu-id="c54e9-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="c54e9-609">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-609">String</span></span>|  
|<span data-ttu-id="c54e9-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="c54e9-611">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-611">String</span></span>|  
|<span data-ttu-id="c54e9-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="c54e9-613">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-613">String</span></span>|  
|<span data-ttu-id="c54e9-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-614">COLLATION_NAME</span></span>|<span data-ttu-id="c54e9-615">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-615">String</span></span>|  
|<span data-ttu-id="c54e9-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="c54e9-617">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-617">String</span></span>|  
|<span data-ttu-id="c54e9-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="c54e9-619">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-619">String</span></span>|  
|<span data-ttu-id="c54e9-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-620">DOMAIN_NAME</span></span>|<span data-ttu-id="c54e9-621">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-621">String</span></span>|  
|<span data-ttu-id="c54e9-622">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-622">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-623">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c54e9-624">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c54e9-624">Procedures</span></span>  
  
|<span data-ttu-id="c54e9-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-625">ColumnName</span></span>|<span data-ttu-id="c54e9-626">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="c54e9-628">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-628">String</span></span>|  
|<span data-ttu-id="c54e9-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="c54e9-630">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-630">String</span></span>|  
|<span data-ttu-id="c54e9-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="c54e9-632">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-632">String</span></span>|  
|<span data-ttu-id="c54e9-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c54e9-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c54e9-634">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-634">Int16</span></span>|  
|<span data-ttu-id="c54e9-635">DEFINIÇÃO_DO_PROCEDIMENTO</span><span class="sxs-lookup"><span data-stu-id="c54e9-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="c54e9-636">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-636">String</span></span>|  
|<span data-ttu-id="c54e9-637">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-637">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-638">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-638">String</span></span>|  
|<span data-ttu-id="c54e9-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="c54e9-639">DATE_CREATED</span></span>|<span data-ttu-id="c54e9-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-640">DateTime</span></span>|  
|<span data-ttu-id="c54e9-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="c54e9-641">DATE_MODIFIED</span></span>|<span data-ttu-id="c54e9-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="c54e9-643">Exibições</span><span class="sxs-lookup"><span data-stu-id="c54e9-643">Views</span></span>  
  
|<span data-ttu-id="c54e9-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-644">ColumnName</span></span>|<span data-ttu-id="c54e9-645">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-646">TABLE_CATALOG</span></span>|<span data-ttu-id="c54e9-647">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-647">String</span></span>|  
|<span data-ttu-id="c54e9-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="c54e9-649">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-649">String</span></span>|  
|<span data-ttu-id="c54e9-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-650">TABLE_NAME</span></span>|<span data-ttu-id="c54e9-651">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-651">String</span></span>|  
|<span data-ttu-id="c54e9-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="c54e9-653">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-653">String</span></span>|  
|<span data-ttu-id="c54e9-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="c54e9-654">CHECK_OPTION</span></span>|<span data-ttu-id="c54e9-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-655">Boolean</span></span>|  
|<span data-ttu-id="c54e9-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="c54e9-656">IS_UPDATABLE</span></span>|<span data-ttu-id="c54e9-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-657">Boolean</span></span>|  
|<span data-ttu-id="c54e9-658">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c54e9-658">DESCRIPTION</span></span>|<span data-ttu-id="c54e9-659">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-659">String</span></span>|  
|<span data-ttu-id="c54e9-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="c54e9-660">DATE_CREATED</span></span>|<span data-ttu-id="c54e9-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-661">DateTime</span></span>|  
|<span data-ttu-id="c54e9-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="c54e9-662">DATE_MODIFIED</span></span>|<span data-ttu-id="c54e9-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="c54e9-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="c54e9-664">Índices</span><span class="sxs-lookup"><span data-stu-id="c54e9-664">Indexes</span></span>  
  
|<span data-ttu-id="c54e9-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c54e9-665">ColumnName</span></span>|<span data-ttu-id="c54e9-666">DataType</span><span class="sxs-lookup"><span data-stu-id="c54e9-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c54e9-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-667">TABLE_CATALOG</span></span>|<span data-ttu-id="c54e9-668">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-668">String</span></span>|  
|<span data-ttu-id="c54e9-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="c54e9-670">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-670">String</span></span>|  
|<span data-ttu-id="c54e9-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-671">TABLE_NAME</span></span>|<span data-ttu-id="c54e9-672">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-672">String</span></span>|  
|<span data-ttu-id="c54e9-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c54e9-673">INDEX_CATALOG</span></span>|<span data-ttu-id="c54e9-674">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-674">String</span></span>|  
|<span data-ttu-id="c54e9-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c54e9-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="c54e9-676">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-676">String</span></span>|  
|<span data-ttu-id="c54e9-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-677">INDEX_NAME</span></span>|<span data-ttu-id="c54e9-678">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-678">String</span></span>|  
|<span data-ttu-id="c54e9-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="c54e9-679">PRIMARY_KEY</span></span>|<span data-ttu-id="c54e9-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-680">Boolean</span></span>|  
|<span data-ttu-id="c54e9-681">EXCLUSIVO</span><span class="sxs-lookup"><span data-stu-id="c54e9-681">UNIQUE</span></span>|<span data-ttu-id="c54e9-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-682">Boolean</span></span>|  
|<span data-ttu-id="c54e9-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="c54e9-683">CLUSTERED</span></span>|<span data-ttu-id="c54e9-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-684">Boolean</span></span>|  
|<span data-ttu-id="c54e9-685">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="c54e9-685">TYPE</span></span>|<span data-ttu-id="c54e9-686">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-686">Int32</span></span>|  
|<span data-ttu-id="c54e9-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="c54e9-687">FILL_FACTOR</span></span>|<span data-ttu-id="c54e9-688">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-688">Int32</span></span>|  
|<span data-ttu-id="c54e9-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="c54e9-689">INITIAL_SIZE</span></span>|<span data-ttu-id="c54e9-690">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-690">Int32</span></span>|  
|<span data-ttu-id="c54e9-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="c54e9-691">NULLS</span></span>|<span data-ttu-id="c54e9-692">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-692">Int32</span></span>|  
|<span data-ttu-id="c54e9-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="c54e9-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="c54e9-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-694">Boolean</span></span>|  
|<span data-ttu-id="c54e9-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="c54e9-695">AUTO_UPDATE</span></span>|<span data-ttu-id="c54e9-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-696">Boolean</span></span>|  
|<span data-ttu-id="c54e9-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="c54e9-697">NULL_COLLATION</span></span>|<span data-ttu-id="c54e9-698">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-698">Int32</span></span>|  
|<span data-ttu-id="c54e9-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="c54e9-700">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-700">Int64</span></span>|  
|<span data-ttu-id="c54e9-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c54e9-701">COLUMN_NAME</span></span>|<span data-ttu-id="c54e9-702">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-702">String</span></span>|  
|<span data-ttu-id="c54e9-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="c54e9-703">COLUMN_GUID</span></span>|<span data-ttu-id="c54e9-704">Guid</span><span class="sxs-lookup"><span data-stu-id="c54e9-704">Guid</span></span>|  
|<span data-ttu-id="c54e9-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="c54e9-705">COLUMN_PROPID</span></span>|<span data-ttu-id="c54e9-706">Int64</span><span class="sxs-lookup"><span data-stu-id="c54e9-706">Int64</span></span>|  
|<span data-ttu-id="c54e9-707">AGRUPAMENTO</span><span class="sxs-lookup"><span data-stu-id="c54e9-707">COLLATION</span></span>|<span data-ttu-id="c54e9-708">Int16</span><span class="sxs-lookup"><span data-stu-id="c54e9-708">Int16</span></span>|  
|<span data-ttu-id="c54e9-709">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="c54e9-709">CARDINALITY</span></span>|<span data-ttu-id="c54e9-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="c54e9-710">Decimal</span></span>|  
|<span data-ttu-id="c54e9-711">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="c54e9-711">PAGES</span></span>|<span data-ttu-id="c54e9-712">Int32</span><span class="sxs-lookup"><span data-stu-id="c54e9-712">Int32</span></span>|  
|<span data-ttu-id="c54e9-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="c54e9-713">FILTER_CONDITION</span></span>|<span data-ttu-id="c54e9-714">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c54e9-714">String</span></span>|  
|<span data-ttu-id="c54e9-715">INTEGRADO</span><span class="sxs-lookup"><span data-stu-id="c54e9-715">INTEGRATED</span></span>|<span data-ttu-id="c54e9-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="c54e9-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c54e9-717">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c54e9-717">See Also</span></span>  
 <span data-ttu-id="c54e9-718">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c54e9-718">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
