function totalLogProb = getTotalLogProb(Param)
    global data nSample
    logProb = zeros(nSample,1);
        for iSample = 1:nSample
            logProb(iSample) = log(normpdf(data(iSample),Param(1),Param(2)));
        end
    totalLogProb = - sum(logProb);
end
