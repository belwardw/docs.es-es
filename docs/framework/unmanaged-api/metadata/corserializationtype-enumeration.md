---
title: "CorSerializationType (Enumeración)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSerializationType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSerializationType
helpviewer_keywords: CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f6650298364f7deb60d553ee21f5028f5cbe7400
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="9b11f-102">CorSerializationType (Enumeración)</span><span class="sxs-lookup"><span data-stu-id="9b11f-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="9b11f-103">Especifica cómo se serializa un objeto por common language runtime.</span><span class="sxs-lookup"><span data-stu-id="9b11f-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b11f-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9b11f-104">Syntax</span></span>  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a><span data-ttu-id="9b11f-105">Miembros</span><span class="sxs-lookup"><span data-stu-id="9b11f-105">Members</span></span>  
  
|<span data-ttu-id="9b11f-106">Miembro</span><span class="sxs-lookup"><span data-stu-id="9b11f-106">Member</span></span>|<span data-ttu-id="9b11f-107">Descripción</span><span class="sxs-lookup"><span data-stu-id="9b11f-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="9b11f-108">La serialización del objeto es indefinida.</span><span class="sxs-lookup"><span data-stu-id="9b11f-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="9b11f-109">El objeto se serializa como un tipo booleano</span><span class="sxs-lookup"><span data-stu-id="9b11f-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="9b11f-110">Objeto se serializa como un tipo de carácter.</span><span class="sxs-lookup"><span data-stu-id="9b11f-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="9b11f-111">Objeto se serializa como un entero de 1 byte con signo.</span><span class="sxs-lookup"><span data-stu-id="9b11f-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="9b11f-112">Objeto se serializa como un entero de 1 byte sin signo.</span><span class="sxs-lookup"><span data-stu-id="9b11f-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="9b11f-113">Objeto se serializa como un entero de 2 bytes con signo.</span><span class="sxs-lookup"><span data-stu-id="9b11f-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="9b11f-114">Objeto se serializa como un entero de 2 bytes sin signo.</span><span class="sxs-lookup"><span data-stu-id="9b11f-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="9b11f-115">Objeto se serializa como un entero de 4 bytes con signo.</span><span class="sxs-lookup"><span data-stu-id="9b11f-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="9b11f-116">Objeto se serializa como un entero de 4 bytes sin signo.</span><span class="sxs-lookup"><span data-stu-id="9b11f-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="9b11f-117">Objeto se serializa como un entero de 8 bits con signo.</span><span class="sxs-lookup"><span data-stu-id="9b11f-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="9b11f-118">Objeto se serializa como un entero de 8 bits sin signo.</span><span class="sxs-lookup"><span data-stu-id="9b11f-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="9b11f-119">Objeto se serializa como un punto flotante de 4 bytes.</span><span class="sxs-lookup"><span data-stu-id="9b11f-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="9b11f-120">Objeto se serializa como un punto flotante de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="9b11f-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="9b11f-121">Objeto se serializa como un tipo System.String.</span><span class="sxs-lookup"><span data-stu-id="9b11f-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="9b11f-122">El objeto se serializa como una sola dimensión, matriz de límite inferior cero.</span><span class="sxs-lookup"><span data-stu-id="9b11f-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="9b11f-123">Objeto se serializa como un tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="9b11f-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="9b11f-124">Objeto se serializa como un objeto etiquetado.</span><span class="sxs-lookup"><span data-stu-id="9b11f-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="9b11f-125">Objeto se serializa como un campo.</span><span class="sxs-lookup"><span data-stu-id="9b11f-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="9b11f-126">Objeto se serializa como una propiedad.</span><span class="sxs-lookup"><span data-stu-id="9b11f-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="9b11f-127">Objeto se serializa como una enumeración.</span><span class="sxs-lookup"><span data-stu-id="9b11f-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b11f-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b11f-128">Requirements</span></span>  
 <span data-ttu-id="9b11f-129">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b11f-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b11f-130">**Encabezado:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9b11f-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9b11f-131">**Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b11f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b11f-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="9b11f-132">See Also</span></span>  
 [<span data-ttu-id="9b11f-133">Enumeraciones para metadatos</span><span class="sxs-lookup"><span data-stu-id="9b11f-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)