# Install dependencies only when needed
FROM node:18-bullseye

ARG NOTABASE_DOWNLOAD_URL
ARG NEXT_PUBLIC_SUPABASE_URL
ARG NEXT_PUBLIC_SUPABASE_KEY
# ARG SUPABASE_SERVICE_KEY

RUN apt update && \
  apt install -y build-essential libcairo2-dev libpango1.0-dev libjpeg-dev libgif-dev librsvg2-dev

RUN wget ${NOTABASE_DOWNLOAD_URL} -O "app.tgz" && \
  mkdir "/app" && \ 
  tar -xzvf "app.tgz" -C "/app" --strip-components 1

WORKDIR /app

# Next.js collects completely anonymous telemetry data about general usage.
# Learn more here: https://nextjs.org/telemetry
# Uncomment the following line in case you want to disable telemetry during the build.
ENV NEXT_TELEMETRY_DISABLED 1

RUN npm ci && \
  NEXT_PUBLIC_SUPABASE_URL=$NEXT_PUBLIC_SUPABASE_URL \
  NEXT_PUBLIC_SUPABASE_KEY=$NEXT_PUBLIC_SUPABASE_KEY \
  npm run build

ENV NODE_ENV production

EXPOSE 3000

ENV PORT 3000

CMD ["npm", "start"]
