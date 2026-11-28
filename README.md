# course-platform-test-customer2

**Fake** second customer (`claude-demo`) for testing [course-platform](https://github.com/vchernoy/course-platform)'s customer isolation (`config/sources.yaml`, see its `docs/content-sources.md`). One repo holds everything for this customer:

```text
config/students.yaml                      students of this customer (example.com only)
config/admins.yaml                        admins of this customer
content/offerings/demo2-course-2027-03/   private course
content/sites/demo2-site/                 public site → /s/demo2-site
```

Isolation checks this repo enables (signed in as the QA account, which is an admin of customer `vchernoy` only):

1. The QA account sees `demo2-course-2027-03` on its dashboard: this customer enrolled it.
2. The QA account is still **denied** `test-locked-2027-04`, even though this repo's `students.yaml` lists it: that course belongs to customer `vchernoy`.
3. `/admin` does **not** list `demo2-course-2027-03` or `demo2-site` for the QA account.
