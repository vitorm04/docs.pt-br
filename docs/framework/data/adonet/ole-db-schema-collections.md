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
ms.openlocfilehash: 9b88308c5dad69ed1ba6f48f525931e94f13ef1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="62124-102">Coleções de esquema de banco de dados OLE</span><span class="sxs-lookup"><span data-stu-id="62124-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="62124-103">Esta seção discute o suporte de coleção de esquema para os provedores OLE DB para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="62124-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="62124-104">Provedor Microsoft SQL Server, OLE DB</span><span class="sxs-lookup"><span data-stu-id="62124-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="62124-105">O Microsoft OLE DB Driver do SQL Server suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="62124-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="62124-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="62124-106">Tables</span></span>  
  
-   <span data-ttu-id="62124-107">Colunas</span><span class="sxs-lookup"><span data-stu-id="62124-107">Columns</span></span>  
  
-   <span data-ttu-id="62124-108">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="62124-108">Procedures</span></span>  
  
-   <span data-ttu-id="62124-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="62124-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="62124-110">Catálogo</span><span class="sxs-lookup"><span data-stu-id="62124-110">Catalog</span></span>  
  
-   <span data-ttu-id="62124-111">Índices</span><span class="sxs-lookup"><span data-stu-id="62124-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="62124-112">Tabelas</span><span class="sxs-lookup"><span data-stu-id="62124-112">Tables</span></span>  
  
|<span data-ttu-id="62124-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-113">ColumnName</span></span>|<span data-ttu-id="62124-114">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-115">TABLE_CATALOG</span></span>|<span data-ttu-id="62124-116">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-116">String</span></span>|  
|<span data-ttu-id="62124-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="62124-118">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-118">String</span></span>|  
|<span data-ttu-id="62124-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-119">TABLE_NAME</span></span>|<span data-ttu-id="62124-120">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-120">String</span></span>|  
|<span data-ttu-id="62124-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62124-121">TABLE_TYPE</span></span>|<span data-ttu-id="62124-122">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-122">String</span></span>|  
|<span data-ttu-id="62124-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-123">TABLE_GUID</span></span>|<span data-ttu-id="62124-124">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-124">Guid</span></span>|  
|<span data-ttu-id="62124-125">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-125">DESCRIPTION</span></span>|<span data-ttu-id="62124-126">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-126">String</span></span>|  
|<span data-ttu-id="62124-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="62124-127">TABLE_PROPID</span></span>|<span data-ttu-id="62124-128">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-128">Int64</span></span>|  
|<span data-ttu-id="62124-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62124-129">DATE_CREATED</span></span>|<span data-ttu-id="62124-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-130">DateTime</span></span>|  
|<span data-ttu-id="62124-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62124-131">DATE_MODIFIED</span></span>|<span data-ttu-id="62124-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="62124-133">Colunas</span><span class="sxs-lookup"><span data-stu-id="62124-133">Columns</span></span>  
  
|<span data-ttu-id="62124-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-134">ColumnName</span></span>|<span data-ttu-id="62124-135">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-136">TABLE_CATALOG</span></span>|<span data-ttu-id="62124-137">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-137">String</span></span>|  
|<span data-ttu-id="62124-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="62124-139">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-139">String</span></span>|  
|<span data-ttu-id="62124-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-140">TABLE_NAME</span></span>|<span data-ttu-id="62124-141">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-141">String</span></span>|  
|<span data-ttu-id="62124-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-142">COLUMN_NAME</span></span>|<span data-ttu-id="62124-143">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-143">String</span></span>|  
|<span data-ttu-id="62124-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-144">COLUMN_GUID</span></span>|<span data-ttu-id="62124-145">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-145">Guid</span></span>|  
|<span data-ttu-id="62124-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62124-146">COLUMN_PROPID</span></span>|<span data-ttu-id="62124-147">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-147">Int64</span></span>|  
|<span data-ttu-id="62124-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62124-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="62124-149">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-149">Int64</span></span>|  
|<span data-ttu-id="62124-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="62124-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="62124-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-151">Boolean</span></span>|  
|<span data-ttu-id="62124-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="62124-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="62124-153">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-153">String</span></span>|  
|<span data-ttu-id="62124-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="62124-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="62124-155">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-155">Int64</span></span>|  
|<span data-ttu-id="62124-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="62124-156">IS_NULLABLE</span></span>|<span data-ttu-id="62124-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-157">Boolean</span></span>|  
|<span data-ttu-id="62124-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="62124-158">DATA_TYPE</span></span>|<span data-ttu-id="62124-159">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-159">Int32</span></span>|  
|<span data-ttu-id="62124-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-160">TYPE_GUID</span></span>|<span data-ttu-id="62124-161">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-161">Guid</span></span>|  
|<span data-ttu-id="62124-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62124-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="62124-163">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-163">Int64</span></span>|  
|<span data-ttu-id="62124-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62124-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="62124-165">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-165">Int64</span></span>|  
|<span data-ttu-id="62124-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62124-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="62124-167">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-167">Int32</span></span>|  
|<span data-ttu-id="62124-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="62124-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="62124-169">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-169">Int16</span></span>|  
|<span data-ttu-id="62124-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62124-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="62124-171">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-171">Int64</span></span>|  
|<span data-ttu-id="62124-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="62124-173">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-173">String</span></span>|  
|<span data-ttu-id="62124-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="62124-175">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-175">String</span></span>|  
|<span data-ttu-id="62124-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="62124-177">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-177">String</span></span>|  
|<span data-ttu-id="62124-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="62124-179">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-179">String</span></span>|  
|<span data-ttu-id="62124-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="62124-181">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-181">String</span></span>|  
|<span data-ttu-id="62124-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-182">COLLATION_NAME</span></span>|<span data-ttu-id="62124-183">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-183">String</span></span>|  
|<span data-ttu-id="62124-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="62124-185">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-185">String</span></span>|  
|<span data-ttu-id="62124-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="62124-187">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-187">String</span></span>|  
|<span data-ttu-id="62124-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-188">DOMAIN_NAME</span></span>|<span data-ttu-id="62124-189">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-189">String</span></span>|  
|<span data-ttu-id="62124-190">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-190">DESCRIPTION</span></span>|<span data-ttu-id="62124-191">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-191">String</span></span>|  
|<span data-ttu-id="62124-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="62124-192">COLUMN_LCID</span></span>|<span data-ttu-id="62124-193">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-193">Int32</span></span>|  
|<span data-ttu-id="62124-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="62124-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="62124-195">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-195">Int32</span></span>|  
|<span data-ttu-id="62124-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="62124-196">COLUMN_SORTID</span></span>|<span data-ttu-id="62124-197">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-197">Int32</span></span>|  
|<span data-ttu-id="62124-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="62124-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="62124-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="62124-199">Byte[]</span></span>|  
|<span data-ttu-id="62124-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="62124-200">IS_COMPUTED</span></span>|<span data-ttu-id="62124-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="62124-202">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="62124-202">Procedures</span></span>  
  
|<span data-ttu-id="62124-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-203">ColumnName</span></span>|<span data-ttu-id="62124-204">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="62124-206">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-206">String</span></span>|  
|<span data-ttu-id="62124-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="62124-208">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-208">String</span></span>|  
|<span data-ttu-id="62124-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="62124-210">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-210">String</span></span>|  
|<span data-ttu-id="62124-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62124-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="62124-212">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-212">Int16</span></span>|  
|<span data-ttu-id="62124-213">DEFINIÇÃO_DO_PROCEDIMENTO</span><span class="sxs-lookup"><span data-stu-id="62124-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="62124-214">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-214">String</span></span>|  
|<span data-ttu-id="62124-215">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-215">DESCRIPTION</span></span>|<span data-ttu-id="62124-216">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-216">String</span></span>|  
|<span data-ttu-id="62124-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62124-217">DATE_CREATED</span></span>|<span data-ttu-id="62124-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-218">DateTime</span></span>|  
|<span data-ttu-id="62124-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62124-219">DATE_MODIFIED</span></span>|<span data-ttu-id="62124-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="62124-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="62124-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="62124-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-222">ColumnName</span></span>|<span data-ttu-id="62124-223">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="62124-225">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-225">String</span></span>|  
|<span data-ttu-id="62124-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="62124-227">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-227">String</span></span>|  
|<span data-ttu-id="62124-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="62124-229">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-229">String</span></span>|  
|<span data-ttu-id="62124-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-230">PARAMETER_NAME</span></span>|<span data-ttu-id="62124-231">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-231">String</span></span>|  
|<span data-ttu-id="62124-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62124-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="62124-233">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-233">Int32</span></span>|  
|<span data-ttu-id="62124-234">TIPO_DE_PARÂMETRO</span><span class="sxs-lookup"><span data-stu-id="62124-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="62124-235">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-235">Int32</span></span>|  
|<span data-ttu-id="62124-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="62124-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="62124-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-237">Boolean</span></span>|  
|<span data-ttu-id="62124-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="62124-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="62124-239">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-239">String</span></span>|  
|<span data-ttu-id="62124-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="62124-240">IS_NULLABLE</span></span>|<span data-ttu-id="62124-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-241">Boolean</span></span>|  
|<span data-ttu-id="62124-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="62124-242">DATA_TYPE</span></span>|<span data-ttu-id="62124-243">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-243">Int32</span></span>|  
|<span data-ttu-id="62124-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62124-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="62124-245">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-245">Int64</span></span>|  
|<span data-ttu-id="62124-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62124-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="62124-247">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-247">Int64</span></span>|  
|<span data-ttu-id="62124-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62124-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="62124-249">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-249">Int32</span></span>|  
|<span data-ttu-id="62124-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="62124-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="62124-251">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-251">Int16</span></span>|  
|<span data-ttu-id="62124-252">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-252">DESCRIPTION</span></span>|<span data-ttu-id="62124-253">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-253">String</span></span>|  
|<span data-ttu-id="62124-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-254">TYPE_NAME</span></span>|<span data-ttu-id="62124-255">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-255">String</span></span>|  
|<span data-ttu-id="62124-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="62124-257">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="62124-258">Catálogo</span><span class="sxs-lookup"><span data-stu-id="62124-258">Catalog</span></span>  
  
|<span data-ttu-id="62124-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-259">ColumnName</span></span>|<span data-ttu-id="62124-260">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-261">CATALOG_NAME</span></span>|<span data-ttu-id="62124-262">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-262">String</span></span>|  
|<span data-ttu-id="62124-263">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-263">DESCRIPTION</span></span>|<span data-ttu-id="62124-264">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="62124-265">Índices</span><span class="sxs-lookup"><span data-stu-id="62124-265">Indexes</span></span>  
  
|<span data-ttu-id="62124-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-266">ColumnName</span></span>|<span data-ttu-id="62124-267">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-268">TABLE_CATALOG</span></span>|<span data-ttu-id="62124-269">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-269">String</span></span>|  
|<span data-ttu-id="62124-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="62124-271">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-271">String</span></span>|  
|<span data-ttu-id="62124-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-272">TABLE_NAME</span></span>|<span data-ttu-id="62124-273">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-273">String</span></span>|  
|<span data-ttu-id="62124-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-274">INDEX_CATALOG</span></span>|<span data-ttu-id="62124-275">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-275">String</span></span>|  
|<span data-ttu-id="62124-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="62124-277">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-277">String</span></span>|  
|<span data-ttu-id="62124-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-278">INDEX_NAME</span></span>|<span data-ttu-id="62124-279">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-279">String</span></span>|  
|<span data-ttu-id="62124-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="62124-280">PRIMARY_KEY</span></span>|<span data-ttu-id="62124-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-281">Boolean</span></span>|  
|<span data-ttu-id="62124-282">EXCLUSIVO</span><span class="sxs-lookup"><span data-stu-id="62124-282">UNIQUE</span></span>|<span data-ttu-id="62124-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-283">Boolean</span></span>|  
|<span data-ttu-id="62124-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="62124-284">CLUSTERED</span></span>|<span data-ttu-id="62124-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-285">Boolean</span></span>|  
|<span data-ttu-id="62124-286">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="62124-286">TYPE</span></span>|<span data-ttu-id="62124-287">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-287">Int32</span></span>|  
|<span data-ttu-id="62124-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="62124-288">FILL_FACTOR</span></span>|<span data-ttu-id="62124-289">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-289">Int32</span></span>|  
|<span data-ttu-id="62124-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="62124-290">INITIAL_SIZE</span></span>|<span data-ttu-id="62124-291">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-291">Int32</span></span>|  
|<span data-ttu-id="62124-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="62124-292">NULLS</span></span>|<span data-ttu-id="62124-293">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-293">Int32</span></span>|  
|<span data-ttu-id="62124-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="62124-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="62124-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-295">Boolean</span></span>|  
|<span data-ttu-id="62124-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="62124-296">AUTO_UPDATE</span></span>|<span data-ttu-id="62124-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-297">Boolean</span></span>|  
|<span data-ttu-id="62124-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="62124-298">NULL_COLLATION</span></span>|<span data-ttu-id="62124-299">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-299">Int32</span></span>|  
|<span data-ttu-id="62124-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62124-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="62124-301">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-301">Int64</span></span>|  
|<span data-ttu-id="62124-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-302">COLUMN_NAME</span></span>|<span data-ttu-id="62124-303">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-303">String</span></span>|  
|<span data-ttu-id="62124-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-304">COLUMN_GUID</span></span>|<span data-ttu-id="62124-305">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-305">Guid</span></span>|  
|<span data-ttu-id="62124-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62124-306">COLUMN_PROPID</span></span>|<span data-ttu-id="62124-307">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-307">Int64</span></span>|  
|<span data-ttu-id="62124-308">AGRUPAMENTO</span><span class="sxs-lookup"><span data-stu-id="62124-308">COLLATION</span></span>|<span data-ttu-id="62124-309">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-309">Int16</span></span>|  
|<span data-ttu-id="62124-310">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="62124-310">CARDINALITY</span></span>|<span data-ttu-id="62124-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="62124-311">Decimal</span></span>|  
|<span data-ttu-id="62124-312">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="62124-312">PAGES</span></span>|<span data-ttu-id="62124-313">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-313">Int32</span></span>|  
|<span data-ttu-id="62124-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="62124-314">FILTER_CONDITION</span></span>|<span data-ttu-id="62124-315">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-315">String</span></span>|  
|<span data-ttu-id="62124-316">INTEGRADO</span><span class="sxs-lookup"><span data-stu-id="62124-316">INTEGRATED</span></span>|<span data-ttu-id="62124-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="62124-318">Provedor OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="62124-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="62124-319">O Microsoft OLE DB Driver Oracle suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="62124-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="62124-320">Tabelas</span><span class="sxs-lookup"><span data-stu-id="62124-320">Tables</span></span>  
  
-   <span data-ttu-id="62124-321">Colunas</span><span class="sxs-lookup"><span data-stu-id="62124-321">Columns</span></span>  
  
-   <span data-ttu-id="62124-322">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="62124-322">Procedures</span></span>  
  
-   <span data-ttu-id="62124-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="62124-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="62124-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="62124-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="62124-325">Exibições</span><span class="sxs-lookup"><span data-stu-id="62124-325">Views</span></span>  
  
-   <span data-ttu-id="62124-326">Índices</span><span class="sxs-lookup"><span data-stu-id="62124-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="62124-327">Tabelas</span><span class="sxs-lookup"><span data-stu-id="62124-327">Tables</span></span>  
  
|<span data-ttu-id="62124-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-328">ColumnName</span></span>|<span data-ttu-id="62124-329">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-330">TABLE_CATALOG</span></span>|<span data-ttu-id="62124-331">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-331">String</span></span>|  
|<span data-ttu-id="62124-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="62124-333">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-333">String</span></span>|  
|<span data-ttu-id="62124-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-334">TABLE_NAME</span></span>|<span data-ttu-id="62124-335">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-335">String</span></span>|  
|<span data-ttu-id="62124-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62124-336">TABLE_TYPE</span></span>|<span data-ttu-id="62124-337">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-337">String</span></span>|  
|<span data-ttu-id="62124-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-338">TABLE_GUID</span></span>|<span data-ttu-id="62124-339">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-339">Guid</span></span>|  
|<span data-ttu-id="62124-340">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-340">DESCRIPTION</span></span>|<span data-ttu-id="62124-341">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-341">String</span></span>|  
|<span data-ttu-id="62124-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="62124-342">TABLE_PROPID</span></span>|<span data-ttu-id="62124-343">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-343">Int64</span></span>|  
|<span data-ttu-id="62124-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62124-344">DATE_CREATED</span></span>|<span data-ttu-id="62124-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-345">DateTime</span></span>|  
|<span data-ttu-id="62124-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62124-346">DATE_MODIFIED</span></span>|<span data-ttu-id="62124-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="62124-348">Colunas</span><span class="sxs-lookup"><span data-stu-id="62124-348">Columns</span></span>  
  
|<span data-ttu-id="62124-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-349">ColumnName</span></span>|<span data-ttu-id="62124-350">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-351">TABLE_CATALOG</span></span>|<span data-ttu-id="62124-352">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-352">String</span></span>|  
|<span data-ttu-id="62124-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="62124-354">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-354">String</span></span>|  
|<span data-ttu-id="62124-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-355">TABLE_NAME</span></span>|<span data-ttu-id="62124-356">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-356">String</span></span>|  
|<span data-ttu-id="62124-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-357">COLUMN_NAME</span></span>|<span data-ttu-id="62124-358">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-358">String</span></span>|  
|<span data-ttu-id="62124-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-359">COLUMN_GUID</span></span>|<span data-ttu-id="62124-360">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-360">Guid</span></span>|  
|<span data-ttu-id="62124-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62124-361">COLUMN_PROPID</span></span>|<span data-ttu-id="62124-362">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-362">Int64</span></span>|  
|<span data-ttu-id="62124-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62124-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="62124-364">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-364">Int64</span></span>|  
|<span data-ttu-id="62124-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="62124-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="62124-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-366">Boolean</span></span>|  
|<span data-ttu-id="62124-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="62124-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="62124-368">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-368">String</span></span>|  
|<span data-ttu-id="62124-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="62124-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="62124-370">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-370">Int64</span></span>|  
|<span data-ttu-id="62124-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="62124-371">IS_NULLABLE</span></span>|<span data-ttu-id="62124-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-372">Boolean</span></span>|  
|<span data-ttu-id="62124-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="62124-373">DATA_TYPE</span></span>|<span data-ttu-id="62124-374">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-374">Int32</span></span>|  
|<span data-ttu-id="62124-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-375">TYPE_GUID</span></span>|<span data-ttu-id="62124-376">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-376">Guid</span></span>|  
|<span data-ttu-id="62124-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62124-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="62124-378">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-378">Int64</span></span>|  
|<span data-ttu-id="62124-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62124-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="62124-380">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-380">Int64</span></span>|  
|<span data-ttu-id="62124-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62124-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="62124-382">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-382">Int32</span></span>|  
|<span data-ttu-id="62124-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="62124-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="62124-384">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-384">Int16</span></span>|  
|<span data-ttu-id="62124-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62124-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="62124-386">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-386">Int64</span></span>|  
|<span data-ttu-id="62124-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="62124-388">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-388">String</span></span>|  
|<span data-ttu-id="62124-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="62124-390">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-390">String</span></span>|  
|<span data-ttu-id="62124-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="62124-392">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-392">String</span></span>|  
|<span data-ttu-id="62124-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="62124-394">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-394">String</span></span>|  
|<span data-ttu-id="62124-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="62124-396">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-396">String</span></span>|  
|<span data-ttu-id="62124-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-397">COLLATION_NAME</span></span>|<span data-ttu-id="62124-398">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-398">String</span></span>|  
|<span data-ttu-id="62124-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="62124-400">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-400">String</span></span>|  
|<span data-ttu-id="62124-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="62124-402">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-402">String</span></span>|  
|<span data-ttu-id="62124-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-403">DOMAIN_NAME</span></span>|<span data-ttu-id="62124-404">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-404">String</span></span>|  
|<span data-ttu-id="62124-405">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-405">DESCRIPTION</span></span>|<span data-ttu-id="62124-406">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="62124-407">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="62124-407">Procedures</span></span>  
  
|<span data-ttu-id="62124-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-408">ColumnName</span></span>|<span data-ttu-id="62124-409">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="62124-411">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-411">String</span></span>|  
|<span data-ttu-id="62124-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="62124-413">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-413">String</span></span>|  
|<span data-ttu-id="62124-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="62124-415">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-415">String</span></span>|  
|<span data-ttu-id="62124-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62124-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="62124-417">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-417">Int16</span></span>|  
|<span data-ttu-id="62124-418">DEFINIÇÃO_DO_PROCEDIMENTO</span><span class="sxs-lookup"><span data-stu-id="62124-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="62124-419">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-419">String</span></span>|  
|<span data-ttu-id="62124-420">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-420">DESCRIPTION</span></span>|<span data-ttu-id="62124-421">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-421">String</span></span>|  
|<span data-ttu-id="62124-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62124-422">DATE_CREATED</span></span>|<span data-ttu-id="62124-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-423">DateTime</span></span>|  
|<span data-ttu-id="62124-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62124-424">DATE_MODIFIED</span></span>|<span data-ttu-id="62124-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="62124-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="62124-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="62124-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-427">ColumnName</span></span>|<span data-ttu-id="62124-428">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="62124-430">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-430">String</span></span>|  
|<span data-ttu-id="62124-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="62124-432">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-432">String</span></span>|  
|<span data-ttu-id="62124-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="62124-434">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-434">String</span></span>|  
|<span data-ttu-id="62124-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-435">COLUMN_NAME</span></span>|<span data-ttu-id="62124-436">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-436">String</span></span>|  
|<span data-ttu-id="62124-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-437">COLUMN_GUID</span></span>|<span data-ttu-id="62124-438">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-438">Guid</span></span>|  
|<span data-ttu-id="62124-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62124-439">COLUMN_PROPID</span></span>|<span data-ttu-id="62124-440">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-440">Int64</span></span>|  
|<span data-ttu-id="62124-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="62124-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="62124-442">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-442">Int64</span></span>|  
|<span data-ttu-id="62124-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62124-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="62124-444">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-444">Int64</span></span>|  
|<span data-ttu-id="62124-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="62124-445">IS_NULLABLE</span></span>|<span data-ttu-id="62124-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-446">Boolean</span></span>|  
|<span data-ttu-id="62124-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="62124-447">DATA_TYPE</span></span>|<span data-ttu-id="62124-448">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-448">Int32</span></span>|  
|<span data-ttu-id="62124-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-449">TYPE_GUID</span></span>|<span data-ttu-id="62124-450">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-450">Guid</span></span>|  
|<span data-ttu-id="62124-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62124-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="62124-452">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-452">Int64</span></span>|  
|<span data-ttu-id="62124-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62124-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="62124-454">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-454">Int64</span></span>|  
|<span data-ttu-id="62124-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62124-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="62124-456">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-456">Int32</span></span>|  
|<span data-ttu-id="62124-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="62124-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="62124-458">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-458">Int16</span></span>|  
|<span data-ttu-id="62124-459">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-459">DESCRIPTION</span></span>|<span data-ttu-id="62124-460">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-460">String</span></span>|  
|<span data-ttu-id="62124-461">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="62124-461">OVERLOAD</span></span>|<span data-ttu-id="62124-462">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="62124-463">Exibições</span><span class="sxs-lookup"><span data-stu-id="62124-463">Views</span></span>  
  
|<span data-ttu-id="62124-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-464">ColumnName</span></span>|<span data-ttu-id="62124-465">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-466">TABLE_CATALOG</span></span>|<span data-ttu-id="62124-467">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-467">String</span></span>|  
|<span data-ttu-id="62124-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="62124-469">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-469">String</span></span>|  
|<span data-ttu-id="62124-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-470">TABLE_NAME</span></span>|<span data-ttu-id="62124-471">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-471">String</span></span>|  
|<span data-ttu-id="62124-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="62124-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="62124-473">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-473">String</span></span>|  
|<span data-ttu-id="62124-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="62124-474">CHECK_OPTION</span></span>|<span data-ttu-id="62124-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-475">Boolean</span></span>|  
|<span data-ttu-id="62124-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="62124-476">IS_UPDATABLE</span></span>|<span data-ttu-id="62124-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-477">Boolean</span></span>|  
|<span data-ttu-id="62124-478">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-478">DESCRIPTION</span></span>|<span data-ttu-id="62124-479">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-479">String</span></span>|  
|<span data-ttu-id="62124-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62124-480">DATE_CREATED</span></span>|<span data-ttu-id="62124-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-481">DateTime</span></span>|  
|<span data-ttu-id="62124-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62124-482">DATE_MODIFIED</span></span>|<span data-ttu-id="62124-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="62124-484">Índices</span><span class="sxs-lookup"><span data-stu-id="62124-484">Indexes</span></span>  
  
|<span data-ttu-id="62124-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-485">ColumnName</span></span>|<span data-ttu-id="62124-486">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-487">TABLE_CATALOG</span></span>|<span data-ttu-id="62124-488">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-488">String</span></span>|  
|<span data-ttu-id="62124-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="62124-490">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-490">String</span></span>|  
|<span data-ttu-id="62124-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-491">TABLE_NAME</span></span>|<span data-ttu-id="62124-492">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-492">String</span></span>|  
|<span data-ttu-id="62124-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-493">INDEX_CATALOG</span></span>|<span data-ttu-id="62124-494">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-494">String</span></span>|  
|<span data-ttu-id="62124-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="62124-496">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-496">String</span></span>|  
|<span data-ttu-id="62124-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-497">INDEX_NAME</span></span>|<span data-ttu-id="62124-498">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-498">String</span></span>|  
|<span data-ttu-id="62124-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="62124-499">PRIMARY_KEY</span></span>|<span data-ttu-id="62124-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-500">Boolean</span></span>|  
|<span data-ttu-id="62124-501">EXCLUSIVO</span><span class="sxs-lookup"><span data-stu-id="62124-501">UNIQUE</span></span>|<span data-ttu-id="62124-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-502">Boolean</span></span>|  
|<span data-ttu-id="62124-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="62124-503">CLUSTERED</span></span>|<span data-ttu-id="62124-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-504">Boolean</span></span>|  
|<span data-ttu-id="62124-505">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="62124-505">TYPE</span></span>|<span data-ttu-id="62124-506">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-506">Int32</span></span>|  
|<span data-ttu-id="62124-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="62124-507">FILL_FACTOR</span></span>|<span data-ttu-id="62124-508">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-508">Int32</span></span>|  
|<span data-ttu-id="62124-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="62124-509">INITIAL_SIZE</span></span>|<span data-ttu-id="62124-510">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-510">Int32</span></span>|  
|<span data-ttu-id="62124-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="62124-511">NULLS</span></span>|<span data-ttu-id="62124-512">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-512">Int32</span></span>|  
|<span data-ttu-id="62124-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="62124-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="62124-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-514">Boolean</span></span>|  
|<span data-ttu-id="62124-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="62124-515">AUTO_UPDATE</span></span>|<span data-ttu-id="62124-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-516">Boolean</span></span>|  
|<span data-ttu-id="62124-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="62124-517">NULL_COLLATION</span></span>|<span data-ttu-id="62124-518">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-518">Int32</span></span>|  
|<span data-ttu-id="62124-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62124-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="62124-520">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-520">Int64</span></span>|  
|<span data-ttu-id="62124-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-521">COLUMN_NAME</span></span>|<span data-ttu-id="62124-522">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-522">String</span></span>|  
|<span data-ttu-id="62124-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-523">COLUMN_GUID</span></span>|<span data-ttu-id="62124-524">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-524">Guid</span></span>|  
|<span data-ttu-id="62124-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62124-525">COLUMN_PROPID</span></span>|<span data-ttu-id="62124-526">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-526">Int64</span></span>|  
|<span data-ttu-id="62124-527">AGRUPAMENTO</span><span class="sxs-lookup"><span data-stu-id="62124-527">COLLATION</span></span>|<span data-ttu-id="62124-528">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-528">Int16</span></span>|  
|<span data-ttu-id="62124-529">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="62124-529">CARDINALITY</span></span>|<span data-ttu-id="62124-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="62124-530">Decimal</span></span>|  
|<span data-ttu-id="62124-531">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="62124-531">PAGES</span></span>|<span data-ttu-id="62124-532">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-532">Int32</span></span>|  
|<span data-ttu-id="62124-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="62124-533">FILTER_CONDITION</span></span>|<span data-ttu-id="62124-534">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-534">String</span></span>|  
|<span data-ttu-id="62124-535">INTEGRADO</span><span class="sxs-lookup"><span data-stu-id="62124-535">INTEGRATED</span></span>|<span data-ttu-id="62124-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="62124-537">Provedor do Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="62124-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="62124-538">O Microsoft Jet OLE DB Driver suporta as seguintes coleções de esquema específico além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="62124-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="62124-539">Tabelas</span><span class="sxs-lookup"><span data-stu-id="62124-539">Tables</span></span>  
  
-   <span data-ttu-id="62124-540">Colunas</span><span class="sxs-lookup"><span data-stu-id="62124-540">Columns</span></span>  
  
-   <span data-ttu-id="62124-541">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="62124-541">Procedures</span></span>  
  
-   <span data-ttu-id="62124-542">Exibições</span><span class="sxs-lookup"><span data-stu-id="62124-542">Views</span></span>  
  
-   <span data-ttu-id="62124-543">Índices</span><span class="sxs-lookup"><span data-stu-id="62124-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="62124-544">Tabelas</span><span class="sxs-lookup"><span data-stu-id="62124-544">Tables</span></span>  
  
|<span data-ttu-id="62124-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-545">ColumnName</span></span>|<span data-ttu-id="62124-546">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-547">TABLE_CATALOG</span></span>|<span data-ttu-id="62124-548">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-548">String</span></span>|  
|<span data-ttu-id="62124-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="62124-550">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-550">String</span></span>|  
|<span data-ttu-id="62124-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-551">TABLE_NAME</span></span>|<span data-ttu-id="62124-552">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-552">String</span></span>|  
|<span data-ttu-id="62124-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62124-553">TABLE_TYPE</span></span>|<span data-ttu-id="62124-554">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-554">String</span></span>|  
|<span data-ttu-id="62124-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-555">TABLE_GUID</span></span>|<span data-ttu-id="62124-556">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-556">Guid</span></span>|  
|<span data-ttu-id="62124-557">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-557">DESCRIPTION</span></span>|<span data-ttu-id="62124-558">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-558">String</span></span>|  
|<span data-ttu-id="62124-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="62124-559">TABLE_PROPID</span></span>|<span data-ttu-id="62124-560">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-560">Int64</span></span>|  
|<span data-ttu-id="62124-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62124-561">DATE_CREATED</span></span>|<span data-ttu-id="62124-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-562">DateTime</span></span>|  
|<span data-ttu-id="62124-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62124-563">DATE_MODIFIED</span></span>|<span data-ttu-id="62124-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="62124-565">Colunas</span><span class="sxs-lookup"><span data-stu-id="62124-565">Columns</span></span>  
  
|<span data-ttu-id="62124-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-566">ColumnName</span></span>|<span data-ttu-id="62124-567">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-568">TABLE_CATALOG</span></span>|<span data-ttu-id="62124-569">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-569">String</span></span>|  
|<span data-ttu-id="62124-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="62124-571">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-571">String</span></span>|  
|<span data-ttu-id="62124-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-572">TABLE_NAME</span></span>|<span data-ttu-id="62124-573">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-573">String</span></span>|  
|<span data-ttu-id="62124-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-574">COLUMN_NAME</span></span>|<span data-ttu-id="62124-575">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-575">String</span></span>|  
|<span data-ttu-id="62124-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-576">COLUMN_GUID</span></span>|<span data-ttu-id="62124-577">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-577">Guid</span></span>|  
|<span data-ttu-id="62124-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62124-578">COLUMN_PROPID</span></span>|<span data-ttu-id="62124-579">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-579">Int64</span></span>|  
|<span data-ttu-id="62124-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62124-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="62124-581">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-581">Int64</span></span>|  
|<span data-ttu-id="62124-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="62124-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="62124-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-583">Boolean</span></span>|  
|<span data-ttu-id="62124-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="62124-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="62124-585">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-585">String</span></span>|  
|<span data-ttu-id="62124-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="62124-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="62124-587">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-587">Int64</span></span>|  
|<span data-ttu-id="62124-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="62124-588">IS_NULLABLE</span></span>|<span data-ttu-id="62124-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-589">Boolean</span></span>|  
|<span data-ttu-id="62124-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="62124-590">DATA_TYPE</span></span>|<span data-ttu-id="62124-591">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-591">Int32</span></span>|  
|<span data-ttu-id="62124-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-592">TYPE_GUID</span></span>|<span data-ttu-id="62124-593">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-593">Guid</span></span>|  
|<span data-ttu-id="62124-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62124-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="62124-595">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-595">Int64</span></span>|  
|<span data-ttu-id="62124-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="62124-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="62124-597">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-597">Int64</span></span>|  
|<span data-ttu-id="62124-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62124-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="62124-599">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-599">Int32</span></span>|  
|<span data-ttu-id="62124-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="62124-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="62124-601">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-601">Int16</span></span>|  
|<span data-ttu-id="62124-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="62124-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="62124-603">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-603">Int64</span></span>|  
|<span data-ttu-id="62124-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="62124-605">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-605">String</span></span>|  
|<span data-ttu-id="62124-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="62124-607">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-607">String</span></span>|  
|<span data-ttu-id="62124-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="62124-609">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-609">String</span></span>|  
|<span data-ttu-id="62124-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="62124-611">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-611">String</span></span>|  
|<span data-ttu-id="62124-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="62124-613">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-613">String</span></span>|  
|<span data-ttu-id="62124-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-614">COLLATION_NAME</span></span>|<span data-ttu-id="62124-615">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-615">String</span></span>|  
|<span data-ttu-id="62124-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="62124-617">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-617">String</span></span>|  
|<span data-ttu-id="62124-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="62124-619">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-619">String</span></span>|  
|<span data-ttu-id="62124-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-620">DOMAIN_NAME</span></span>|<span data-ttu-id="62124-621">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-621">String</span></span>|  
|<span data-ttu-id="62124-622">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-622">DESCRIPTION</span></span>|<span data-ttu-id="62124-623">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="62124-624">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="62124-624">Procedures</span></span>  
  
|<span data-ttu-id="62124-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-625">ColumnName</span></span>|<span data-ttu-id="62124-626">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="62124-628">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-628">String</span></span>|  
|<span data-ttu-id="62124-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="62124-630">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-630">String</span></span>|  
|<span data-ttu-id="62124-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="62124-632">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-632">String</span></span>|  
|<span data-ttu-id="62124-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="62124-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="62124-634">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-634">Int16</span></span>|  
|<span data-ttu-id="62124-635">DEFINIÇÃO_DO_PROCEDIMENTO</span><span class="sxs-lookup"><span data-stu-id="62124-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="62124-636">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-636">String</span></span>|  
|<span data-ttu-id="62124-637">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-637">DESCRIPTION</span></span>|<span data-ttu-id="62124-638">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-638">String</span></span>|  
|<span data-ttu-id="62124-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62124-639">DATE_CREATED</span></span>|<span data-ttu-id="62124-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-640">DateTime</span></span>|  
|<span data-ttu-id="62124-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62124-641">DATE_MODIFIED</span></span>|<span data-ttu-id="62124-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="62124-643">Exibições</span><span class="sxs-lookup"><span data-stu-id="62124-643">Views</span></span>  
  
|<span data-ttu-id="62124-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-644">ColumnName</span></span>|<span data-ttu-id="62124-645">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-646">TABLE_CATALOG</span></span>|<span data-ttu-id="62124-647">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-647">String</span></span>|  
|<span data-ttu-id="62124-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="62124-649">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-649">String</span></span>|  
|<span data-ttu-id="62124-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-650">TABLE_NAME</span></span>|<span data-ttu-id="62124-651">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-651">String</span></span>|  
|<span data-ttu-id="62124-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="62124-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="62124-653">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-653">String</span></span>|  
|<span data-ttu-id="62124-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="62124-654">CHECK_OPTION</span></span>|<span data-ttu-id="62124-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-655">Boolean</span></span>|  
|<span data-ttu-id="62124-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="62124-656">IS_UPDATABLE</span></span>|<span data-ttu-id="62124-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-657">Boolean</span></span>|  
|<span data-ttu-id="62124-658">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="62124-658">DESCRIPTION</span></span>|<span data-ttu-id="62124-659">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-659">String</span></span>|  
|<span data-ttu-id="62124-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="62124-660">DATE_CREATED</span></span>|<span data-ttu-id="62124-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-661">DateTime</span></span>|  
|<span data-ttu-id="62124-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="62124-662">DATE_MODIFIED</span></span>|<span data-ttu-id="62124-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="62124-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="62124-664">Índices</span><span class="sxs-lookup"><span data-stu-id="62124-664">Indexes</span></span>  
  
|<span data-ttu-id="62124-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="62124-665">ColumnName</span></span>|<span data-ttu-id="62124-666">DataType</span><span class="sxs-lookup"><span data-stu-id="62124-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="62124-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-667">TABLE_CATALOG</span></span>|<span data-ttu-id="62124-668">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-668">String</span></span>|  
|<span data-ttu-id="62124-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="62124-670">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-670">String</span></span>|  
|<span data-ttu-id="62124-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-671">TABLE_NAME</span></span>|<span data-ttu-id="62124-672">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-672">String</span></span>|  
|<span data-ttu-id="62124-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="62124-673">INDEX_CATALOG</span></span>|<span data-ttu-id="62124-674">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-674">String</span></span>|  
|<span data-ttu-id="62124-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="62124-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="62124-676">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-676">String</span></span>|  
|<span data-ttu-id="62124-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-677">INDEX_NAME</span></span>|<span data-ttu-id="62124-678">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-678">String</span></span>|  
|<span data-ttu-id="62124-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="62124-679">PRIMARY_KEY</span></span>|<span data-ttu-id="62124-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-680">Boolean</span></span>|  
|<span data-ttu-id="62124-681">EXCLUSIVO</span><span class="sxs-lookup"><span data-stu-id="62124-681">UNIQUE</span></span>|<span data-ttu-id="62124-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-682">Boolean</span></span>|  
|<span data-ttu-id="62124-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="62124-683">CLUSTERED</span></span>|<span data-ttu-id="62124-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-684">Boolean</span></span>|  
|<span data-ttu-id="62124-685">TIPO DE</span><span class="sxs-lookup"><span data-stu-id="62124-685">TYPE</span></span>|<span data-ttu-id="62124-686">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-686">Int32</span></span>|  
|<span data-ttu-id="62124-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="62124-687">FILL_FACTOR</span></span>|<span data-ttu-id="62124-688">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-688">Int32</span></span>|  
|<span data-ttu-id="62124-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="62124-689">INITIAL_SIZE</span></span>|<span data-ttu-id="62124-690">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-690">Int32</span></span>|  
|<span data-ttu-id="62124-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="62124-691">NULLS</span></span>|<span data-ttu-id="62124-692">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-692">Int32</span></span>|  
|<span data-ttu-id="62124-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="62124-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="62124-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-694">Boolean</span></span>|  
|<span data-ttu-id="62124-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="62124-695">AUTO_UPDATE</span></span>|<span data-ttu-id="62124-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-696">Boolean</span></span>|  
|<span data-ttu-id="62124-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="62124-697">NULL_COLLATION</span></span>|<span data-ttu-id="62124-698">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-698">Int32</span></span>|  
|<span data-ttu-id="62124-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="62124-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="62124-700">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-700">Int64</span></span>|  
|<span data-ttu-id="62124-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="62124-701">COLUMN_NAME</span></span>|<span data-ttu-id="62124-702">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-702">String</span></span>|  
|<span data-ttu-id="62124-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="62124-703">COLUMN_GUID</span></span>|<span data-ttu-id="62124-704">GUID</span><span class="sxs-lookup"><span data-stu-id="62124-704">Guid</span></span>|  
|<span data-ttu-id="62124-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="62124-705">COLUMN_PROPID</span></span>|<span data-ttu-id="62124-706">Int64</span><span class="sxs-lookup"><span data-stu-id="62124-706">Int64</span></span>|  
|<span data-ttu-id="62124-707">AGRUPAMENTO</span><span class="sxs-lookup"><span data-stu-id="62124-707">COLLATION</span></span>|<span data-ttu-id="62124-708">Int16</span><span class="sxs-lookup"><span data-stu-id="62124-708">Int16</span></span>|  
|<span data-ttu-id="62124-709">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="62124-709">CARDINALITY</span></span>|<span data-ttu-id="62124-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="62124-710">Decimal</span></span>|  
|<span data-ttu-id="62124-711">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="62124-711">PAGES</span></span>|<span data-ttu-id="62124-712">Int32</span><span class="sxs-lookup"><span data-stu-id="62124-712">Int32</span></span>|  
|<span data-ttu-id="62124-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="62124-713">FILTER_CONDITION</span></span>|<span data-ttu-id="62124-714">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62124-714">String</span></span>|  
|<span data-ttu-id="62124-715">INTEGRADO</span><span class="sxs-lookup"><span data-stu-id="62124-715">INTEGRATED</span></span>|<span data-ttu-id="62124-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="62124-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62124-717">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62124-717">See Also</span></span>  
 <span data-ttu-id="62124-718">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="62124-718">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
