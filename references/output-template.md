# Publication receipt template

After attempting the upload, provide these sections inline in this order:

1. 上传状态 — 已发布、仅准备、等待登录、被校验阻止或失败
2. YouMind 地址 — verified listing URL when published
3. 已提交字段 — skill name, subtitle, instructions, input prompt, and description
4. 已上传图片 — avatar, cover, and any representative showcases
5. 校验 — character counts, pixel dimensions, aspect ratios, and protected-prompt fidelity
6. 后续修改 — exact listing to edit and any intentionally omitted optional showcase slots

When filesystem access is available, save:

```text
<skill-name>-youmind-upload/
|-- listing.md
|-- image-prompts.md
|-- upload-receipt.md
`-- assets/
    |-- avatar-1024.png
    |-- cover-1600x900.png
    `-- showcase-01-1600x900.png
```

Omit unused showcase slots. Do not create blank placeholders.
