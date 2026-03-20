FROM frappe/erpnext:v15

USER frappe
WORKDIR /home/frappe/frappe-bench

# lms: app_name="frappe_lms"이지만 모듈 디렉토리는 "lms"
# symlink으로 frappe_lms -> lms 별칭 생성해야 import 정상 작동
RUN git clone --depth 1 --branch main https://github.com/frappe/lms apps/lms \
    && ln -s /home/frappe/frappe-bench/apps/lms/lms \
             /home/frappe/frappe-bench/apps/lms/frappe_lms \
    && git clone --depth 1 --branch version-14 https://github.com/frappe/wiki apps/wiki \
    && /home/frappe/frappe-bench/env/bin/pip install --no-cache-dir \
       -e apps/lms \
       -e apps/wiki \
    && /home/frappe/frappe-bench/env/bin/pip install --no-cache-dir --upgrade "redis>=4.0.0"
