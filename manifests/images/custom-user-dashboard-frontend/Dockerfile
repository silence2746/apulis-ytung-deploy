FROM node:12

RUN mkdir -p /home/custom-user-dashboard
WORKDIR /home/custom-user-dashboard
RUN git clone --branch develop https://f2e519fa5bbd47052bd908523fa3ec26c3204ba4@github.com/apulis/addon_custom_user_group_dashboard.git /home/custom-user-dashboard
RUN yarn config set registry 'https://registry.npm.taobao.org'
RUN yarn
RUN yarn build

EXPOSE 3083

CMD ["yarn", "run", "static"]
